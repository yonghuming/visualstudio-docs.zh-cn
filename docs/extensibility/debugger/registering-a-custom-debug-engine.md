---
title: "注册自定义调试引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎注册"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# 注册自定义调试引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试引擎必须将自身注册为遵循 COM 约定的类工厂以及通过 Visual Studio 注册表子项与 Visual Studio 注册。  
  
> [!NOTE]
>  举例说明如何注册的调试引擎可以找到在 TextInterpreter 示例中，将生成的一部分为 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/zh-cn/9097b71e-1fe7-48f7-bc00-009e25940c24)。  
  
## DLL 服务器进程  
 通常，调试引擎实现是在其自己的 DLL 作为 COM 服务器。 这意味着，调试引擎必须其类工厂的 CLSID 向 COM 注册 Visual Studio 才能访问它。 然后调试引擎必须自行注册使用 Visual Studio 中以便对消息进行任何属性 （也称为度量值） 调试引擎支持。 写入到的调试引擎的 Visual Studio 注册表子项的度量值的选择取决于调试引擎支持的功能。  
  
 [SDK 帮助器调试](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 描述不仅注册表位置必须注册的调试引擎;它还介绍 dbgmetric.lib 库，它包含大量有用的函数和 c \+ \+ 开发人员，使操作更容易注册表的声明。  
  
### 示例  
 以下是一个典型示例 （从 TextInterpreter 示例） 演示如何使用 `SetMetric` 函数 （从 dbgmetric.lib\)，以注册 Visual Studio 的调试引擎。 Dbgmetric.lib 中也定义了所传递的度量值。  
  
> [!NOTE]
>  TextInterpreter 是一种基本的调试引擎;它没有实现，并因此不会注册 — 任何其他功能。 更完整的调试引擎应具有的一个整个列表 `SetMetric` 调用或其等效表达式，其中一个调试引擎每项功能支持。  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## 请参阅  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [SDK 帮助器调试](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/zh-cn/9097b71e-1fe7-48f7-bc00-009e25940c24)