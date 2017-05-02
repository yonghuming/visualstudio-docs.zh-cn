---
title: "针对 Edge 和JsRT API 中的旧引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbc7df6c-0bc9-48f5-b9ad-b9ed31c42f92
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 针对 Edge 和JsRT API 中的旧引擎
从 Windows 10 开始，我们对 Chakra（JavaScript 引擎）进行的其中一项更改（与支持新 Edge 呈现引擎的 Windows 10 浏览器战略保持一致）是支持两个不同的 Chakra 引擎：  
  
-   旧的 Chakra 引擎（也称为*“旧引擎”*或下面的 jscript9.dll），它附带并支持 Internet Explorer 11。 此引擎在时间上处于冻结状态，并且将与 Win8.1\/IE11 版基本上保持不变。  
  
-   新的 Chakra 引擎（也称为*“Edge 引擎”*或下面的 chakra.dll），它附带并支持 Windows 10、Microsoft Edge 中的新浏览器。 此引擎将不断地被更新并且将支持“动态”[Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx) 引擎。 与旧引擎不同，动态 Edge 引擎意味着，Edge 引擎将不传递要选择的任何形式的版本控制脚本功能。  
  
 使用 JavaScript 运行时承载 \(JsRT\) API 创建应用时，可以选择以旧引擎还是 Edge 引擎为目标。  
  
-   如果需要强调现有应用程序的向后兼容性，则以旧引擎为目标。  
  
-   如果希望应用“向前看”并且当发布新 JavaScript（如 CMAScript 6）时支持它们的新功能，则以 Edge 引擎为目标。  
  
 本主题包括说明如何以不同的引擎为目标的详细信息。  
  
## 以首选版本为目标  
 创建应用时，可以选择支持 Edge 引擎或旧引擎的 JsRT 版本。 可以根据上述准则选择 JsRT 版本。 为了适应这些区别，已对 `JsCreateRuntime`、`JsCreateContext` 和 `JsStartDebugging` 进行了以下更改。  
  
 对于 `JsCreateRuntime`：  
  
-   当以旧引擎为目标时，弃用 `JsRuntimeVersionEdge` 枚举值，并且消息将建议改用 `JsRuntimeVersionInternetExplorer11` 值。  
  
-   当以 Edge 引擎为目标时，版本参数从 `JsCreateRuntime` 函数省略。  
  
    ```cpp  
    JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
    ```  
  
 对于 `JsCreateContext` 和 `JsStartDebugging`：  
  
-   当以旧引擎为目标时，使用 `IDebugApplication` 接口来提供自己的非远程调试方法。 出于调试目的，`JsCreateContext` 和 `JsStartDebugging` 函数采用 `IDebugApplication` 作为参数。  
  
-   当以旧引擎为目标时，弃用 `IDebugApplication` 接口。 Chakra 引擎能够通过 Visual Studio 调试器启用本机和脚本调试功能，而无需从用户处实现 `IDebugApplication`。 结果是，接口不再是 `JsCreateContext` 和 `JsStartDebugging` 的参数。  
  
 旧引擎中上述 API 的签名如下：  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsRuntimeVersion version, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, IDebugApplication *debugApplication, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging(IDebugApplication *debugApplication);  
```  
  
 Edge 引擎中上述 API 签名如下：  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging();  
```  
  
## 使用 Visual C\+\+ 编译首选版本  
 使用 Visual C\+\+ 时，通过包括 jsrt.h 标头来导入 JsRT API，并确保 jsrt.lib 包含在链接器输入文件列表中：  
  
```cpp  
#include <jsrt.h>  
```  
  
 ![将 jsrt.lib 添加为链接器输入文件](../chakra-hosting/media/js-chakra.png "JS\_Chakra\_")  
  
 如果要面向 Edge 引擎二进制文件，则需要定义宏 `USE_EDGEMODE_JSRT`，然后才能包括 jsrt.h，并且你应针对 chakrart.lib 进行链接，而不是针对 jsrt.lib 进行链接：  
  
```cpp  
#define USE_EDGEMODE_JSRT  
#include <jsrt.h>  
```  
  
 ![将 chakrart.lib 添加为链接器输入文件](../chakra-hosting/media/js-chakra-hosting.png "JS\_Chakra\_Hosting\_")  
  
 如果刚开始使用新的应用程序，现在就可以针对 JsRT API 开始编写代码。  
  
## 使用 .NET 编译首选版本  
 如果使用的是 .NET 和 P\/Invoke，则必须更改 JsRT API \[DllImport\] 声明以导入 chakra.dll，而不是导入 jscript9.dll。 此外，更改 `JsCreateRuntime` 的定义以删除 `JsRuntimeVersion` 参数，更改 `JsCreateContext` 和 `JsStartDebugging` 的定义以删除 `IDebugApplication` 参数。  
  
 对于旧引擎，使用下面的代码。  
  
```csharp  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsRuntimeVersion version,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    IDebugApplication debugApplication,  
    out JsContextRef newContext  
);   
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsStartDebugging(  
    IDebugApplication debugApplication,  
);  
```  
  
 对于 Edge 引擎，使用下面的代码。  
  
```csharp  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    out JsContextRef newContext  
);   
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsStartDebugging();  
```  
  
> [!CAUTION]
>  如果手动封送函数指针（如通过 LoadLibrary\/GetProcAddress），则谨记不要混用方法的声明，否则将致使堆栈失衡，从而导致不可预知的行为（如导致应用崩溃）。 如果在导入代码中执行 jscript9.dll 实例的全局搜索和替换，会发生同样的问题，因为将遗漏正删除的 `version` 参数。  
  
## 摘要  
 在 Windows 10 中，JavaScript 运行时承载 API 拆分为两个。 这些 API 现在支持“动态”Edge 引擎，其语言功能将与 Microsoft Edge 中的"动态"Edge 引擎保持一致。 可从桌面或应用商店应用来利用这些功能，以创建令人兴奋的新方法，从而扩展应用程序及利用现有代码库中的现代 Web 技能。 但是，由于以前版本间存在细微差别，因此在以 Edge 引擎或旧引擎为目标时必须注意以下几点。  
  
-   应用的每个进程只能支持一个 JsRT 版本。  
  
     例如，不能先创建一个 Edge 引擎运行时，然后创建一个旧引擎运行时，并希望它们在同一进程中正常运行。 这不受支持，并可能导致未记录的行为，如加载第二个 DLL 失败。  
  
-   如果以 Edge 引擎为目标，则在自动更新基础平台时，应用可能会意外获取新功能。  
  
     例如，旧运行时的 Internet Explorer 11 模式支持块范围变量声明，如 `let` 和 `const`。 如果 Edge 引擎自动版本控制行为之前就是标准的，则当平台已自动升级时，Internet Explorer 10 模式中已运行的且没有块范围规则的代码可能已经开始失败。 选择使用的运行时模型时，必须要考虑这一点。 虽然我们相信只要有可能都应以 Edge 引擎为目标，但使用未来可能失效的 JavaScript 代码结构时必须小心。  
  
-   Windows 应用商店的 JsRT 仅支持 Edge 引擎 \(chakra.dll\)。 尝试针对 jscript9.dll 中任何 JsRT API 进行链接的应用将无法通过认证。  
  
-   至关重要的是，切勿混淆 jscript9.dll 与 chakra.dll 之间 `JsCreateRuntime`、`JsCreateContext` 和 `JsStartDebugging` 的声明，因为这将导致堆栈失衡。  
  
     使用 C 和 C\+\+ 时，如果尝试使用错误的声明，只要未执行诸如调用 `LoadLibrary` 再调用 `GetProcAddress` 的行为，都将收到一个链接器错误。 .NET 开发人员可能不会轻易发现此问题，因此使用此功能时请仔细检查代码。  
  
## 请参阅  
 [JavaScript 运行时承载](../chakra-hosting/javascript-runtime-hosting.md)