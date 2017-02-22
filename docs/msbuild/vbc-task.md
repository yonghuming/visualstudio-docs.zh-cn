---
title: "Vbc 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Vbc 任务"
  - "Vbc 任务 [MSBuild]"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vbc 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包装产生可执行文件 \(.exe\)、动态链接库 \(.dll\) 或代码模块 \(.netmodule\) 的 vbc.exe。  netmodule\)。  有关 vbc.exe 的更多信息，请参见 [Visual Basic 命令行编译器](/dotnet/visual-basic/reference/command-line-compiler/index)。  
  
## 参数  
 下表描述了 `Vbc` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`AdditionalLibPaths`|可选 `String[]` 参数。<br /><br /> 指定其他文件夹，将在这些文件夹中查找 References 特性中指定的程序集。|  
|`AddModules`|可选 `String[]` 参数。<br /><br /> 使编译器将指定文件中的所有类型信息对当前正在编译的项目可用。  此参数对应于 vbc.exe 编译器的 [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) 开关。|  
|`BaseAddress`|可选 `String` 参数。<br /><br /> 指定 DLL 的基址。  此参数对应于 vbc.exe 编译器的 [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) 开关。|  
|`CodePage`|可选 `Int32` 参数。<br /><br /> 指定要用于编译中所有源代码文件的代码页。  此参数对应于 vbc.exe 编译器的 [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) 开关。|  
|`DebugType`|可选 `String[]` 参数。<br /><br /> 使编译器生成调试信息。  此参数可以具有下列值：<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> 默认值为 `full`，允许将调试器附加到正在运行的程序。  `pdbonly` 值允许在调试器中启动程序的时候进行源代码调试，但是，只有当将正在运行的程序附加到调试器时，才显示汇编语言代码。  有关更多信息，请参见 [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug)。|  
|`DefineConstants`|可选 `String[]` 参数。<br /><br /> 定义条件编译器常数。  符号\/值对是使用下面的语法指定的，并且彼此之间用分号分隔：<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> 此参数对应于 vbc.exe 编译器的 [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) 开关。|  
|`DelaySign`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，任务会将公钥放置在程序集中。  如果设置为 `false`，则任务会对程序集进行完整签名。  默认值为 `false`。除非与 `KeyFile` 参数或 `KeyContainer` 参数结合使用，否则此参数不会产生任何效果。  此参数对应于 vbc.exe 编译器的 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) 开关。|  
|`DisabledWarnings`|可选 `String` 参数。<br /><br /> 禁止显示指定的警告。  仅需要指定警告标识符的数值部分。  多个警告之间用分号分隔。  此参数对应于 vbc.exe 编译器的 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) 开关。|  
|`DocumentationFile`|可选 `String` 参数。<br /><br /> 将文档注释处理到一个指定的 XML 文件中。  此参数重写 `GenerateDocumentation` 特性。  有关更多信息，请参见 [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。|  
|`EmitDebugInformation`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，任务将生成调试信息，并将该信息放置在 .pdb 文件中。  有关更多信息，请参见 [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug)。|  
|`ErrorReport`|可选 `String` 参数。<br /><br /> 指定任务报告内部编译器错误的方式。  此参数可以具有下列值：<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> 如果指定了 `prompt`，那么当发生内部编译器错误时，系统将通过一个选项来询问用户是否将错误数据发送到 Microsoft。<br /><br /> 如果指定了 `send`，那么当发生内部编译器错误时，任务会将错误数据发送到 Microsoft。<br /><br /> 默认值为 `none`，这意味着仅在文本输出中报告错误。<br /><br /> 此参数对应于 vbc.exe 编译器的 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) 开关。|  
|`FileAlignment`|可选 `Int32` 参数。<br /><br /> 指定输出文件各部分的对齐位置，以字节为单位。  此参数可以具有下列值：<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> 此参数对应于 vbc.exe 编译器的 [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) 开关。|  
|`GenerateDocumentation`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，将生成文档信息，并将此信息放置在与任务正在创建的可执行文件或库的名称相同的 XML 文件中。  有关更多信息，请参见 [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。|  
|`Imports`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 从指定的项集合导入命名空间。  此参数对应于 vbc.exe 编译器的 [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) 开关。|  
|`KeyContainer`|可选 `String` 参数。<br /><br /> 指定加密密钥容器的名称。  此参数对应于 vbc.exe 编译器的 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) 开关。|  
|`KeyFile`|可选 `String` 参数。<br /><br /> 指定包含加密密钥的文件名。  有关更多信息，请参见 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)。|  
|`LangVersion`|可选 [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 参数。<br /><br /> 指定语言版本，“9”或“10”。|  
|`LinkResources`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 在输出文件中创建指向 .NET Framework 资源的链接；资源文件没有放置在输出文件中。  此参数对应于 vbc.exe 编译器的 [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) 开关。|  
|`MainEntryPoint`|可选 `String` 参数。<br /><br /> 指定包含 `Sub Main` 过程的类或模块。  此参数对应于 vbc.exe 编译器的 [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) 开关。|  
|`ModuleAssemblyName`|可选 `String` 参数。<br /><br /> 指定包含此模块的程序集。|  
|`NoConfig`|可选 `Boolean` 参数。<br /><br /> 指定编译器不应使用 vbc.rsp 文件。  此参数对应于 vbc.exe 编译器的 [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) 参数。|  
|`NoLogo`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，将禁止显示编译器版本标志信息。  此参数对应于 vbc.exe 编译器的 [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) 开关。|  
|`NoStandardLib`|可选 `Boolean` 参数。<br /><br /> 使编译器不引用标准库。  此参数对应于 vbc.exe 编译器的 [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) 开关。|  
|`NoVBRuntimeReference`|可选 `Boolean` 参数。<br /><br /> 仅供内部使用。  如果为 true，则防止自动引用 Microsoft.VisualBasic.dll。|  
|`NoWarnings`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，任务将禁止显示所有警告。  有关更多信息，请参见 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。|  
|`Optimize`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，将启用编译器优化。  此参数对应于 vbc.exe 编译器的 [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) 开关。|  
|`OptionCompare`|可选 `String` 参数。<br /><br /> 指定如何进行字符串比较。  此参数可以具有下列值：<br /><br /> -   `binary`<br />-   `text`<br /><br /> 如果值为 `binary`，表示任务应使用二进制字符串比较。  如果值为 `text`，表示任务应使用文本字符串比较。  此参数的默认值为 `binary`。  此参数对应于 vbc.exe 编译器的 [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) 开关。|  
|`OptionExplicit`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，将需要显式声明变量。  此参数对应于 vbc.exe 编译器的 [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) 开关。|  
|`OptionInfer`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则允许变量的类型推断。|  
|`OptionStrict`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，任务将强制使用严格类型语义以限制隐式类型转换。  此参数对应于 vbc.exe 编译器的 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) 开关。|  
|`OptionStrictType`|可选 `String` 参数。<br /><br /> 指定哪些严格的类型语义生成警告。  当前，仅支持“自定义”。  此参数对应于 vbc.exe 编译器的 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) 开关。|  
|`OutputAssembly`|可选 `String` 输出参数。<br /><br /> 指定输出文件的名称。  此参数对应于 vbc.exe 编译器的 [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) 开关。|  
|`Platform`|可选 `String` 参数。<br /><br /> 指定输出文件的目标处理器平台。  此参数的值可以为 `x86`、`x64`、`Itanium` 或 `anycpu`。  默认值为 `anycpu`。  此参数对应于 vbc.exe 编译器的 [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) 开关。|  
|`References`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 使任务将公共类型信息从指定项导入到当前项目。  此参数对应于 vbc.exe 编译器的 [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) 开关。|  
|`RemoveIntegerChecks`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，将禁止执行整数溢出错误检查。  默认值为 `false`。  此参数对应于 vbc.exe 编译器的 [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) 开关。|  
|`Resources`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 将一个 .NET Framework 资源嵌入到输出文件中。  此参数对应于 vbc.exe 编译器的 [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) 开关。|  
|`ResponseFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定包含此任务的命令的响应文件。  此参数对应于 vbc.exe 编译器的 [@（指定响应文件）](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file)选项。|  
|`RootNamespace`|可选 `String` 参数。<br /><br /> 为所有类型声明指定根命名空间。  此参数对应于 vbc.exe 编译器的 [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) 开关。|  
|`SdkPath`|可选 `String` 参数。<br /><br /> 指定 mscorlib.dll 和 microsoft.visualbasic.dll 的位置。  此参数对应于 vbc.exe 编译器的 [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) 开关。|  
|`Sources`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定一个或多个 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 源文件。|  
|`TargetCompactFramework`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，则任务面向 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]。  此开关对应于 vbc.exe 编译器的 [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) 开关。|  
|`TargetType`|可选 `String` 参数。<br /><br /> 指定输出文件的文件格式。  此参数的值可以为 `library`（创建代码库）、`exe`（创建控制台应用程序）、`module`（创建模块）或 `winexe`（创建 Windows 程序）。  默认值为 `library`。  此参数对应于 vbc.exe 编译器的 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) 开关。|  
|`Timeout`|可选 `Int32` 参数。<br /><br /> 指定在多少毫秒后终止任务可执行文件。  默认值为 `Int.MaxValue`，这表示没有超时期限。|  
|`ToolPath`|可选 `String` 参数。<br /><br /> 指定任务将从什么位置加载基础可执行文件 \(vbc.exe\)。  如果未指定此参数，任务将使用与运行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的 Framework 版本对应的 SDK 安装路径。|  
|`TreatWarningsAsErrors`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，则所有警告都将被视为错误。  有关更多信息，请参见 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。|  
|`UseHostCompilerIfAvailable`|可选 `Boolean` 参数。<br /><br /> 指示任务使用进程内编译器对象（如果有的话）。  仅由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用。|  
|`Utf8Output`|可选 `Boolean` 参数。<br /><br /> 使用 UTF\-8 编码记录编译器输出。  此参数对应于 vbc.exe 编译器的 [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) 开关。|  
|`Verbosity`|可选 `String` 参数。<br /><br /> 指定编译器输出的详细级别。  详细级别可以为 `Quiet`、`Normal`（默认值）或 `Verbose`。|  
|`WarningsAsErrors`|可选 `String` 参数。<br /><br /> 指定将被视为错误的警告的列表。  有关更多信息，请参见 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 此参数重写 `TreatWarningsAsErrors` 参数。|  
|`WarningsNotAsErrors`|可选 `String` 参数。<br /><br /> 指定不被视为错误的警告的列表。  有关更多信息，请参见 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 只有当 `TreatWarningsAsErrors` 参数设置为 `true` 时，此参数才有用。|  
|`Win32Icon`|可选 `String` 参数。<br /><br /> 插入.ico文件程序集中，则输出文件在文件Explorer所需的外观。  此参数对应于 vbc.exe 编译器的 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) 开关。|  
|`Win32Resources`|可选 `String` 参数。<br /><br /> 在输出文件中插入 Win32 资源文件 \(.res\)。  此参数对应于 vbc.exe 编译器的 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) 开关。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.ToolTask> 类继承。  有关这些附加参数及其说明的列表，请参见 [ToolTaskExtension 基类](../msbuild/tooltaskextension-base-class.md)。  
  
## 示例  
 下面的示例编译一个 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 项目。  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## 请参阅  
 [Visual Basic 命令行编译器](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)