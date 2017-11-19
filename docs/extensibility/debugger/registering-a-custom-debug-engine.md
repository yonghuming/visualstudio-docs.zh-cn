---
title: "注册的自定义调试引擎 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58f58a1a6ec80331fd5cf6f735098c16c35db82e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-custom-debug-engine"></a>注册自定义调试引擎
调试引擎必须将自身注册为以下 COM 约定的类工厂以及通过 Visual Studio 注册表子项注册 Visual Studio。  
  
> [!NOTE]
>  举例说明如何注册调试引擎可以找到在 TextInterpreter 示例中，生成的一部分为[教程： 生成调试引擎使用 ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)。  
  
## <a name="dll-server-process"></a>DLL 服务器进程  
 通常，调试引擎中实施自己的 DLL 作为 COM 服务器。 这意味着的调试引擎必须其类工厂的 CLSID 向 COM 注册 Visual Studio 才能访问它。 然后的调试引擎必须向注册自己 Visual Studio 自身才能建立任何属性 （也称为度量值） 调试引擎支持。 写入到的调试引擎的 Visual Studio 注册表子项的度量值的选择取决于调试引擎支持的功能。  
  
 [SDK 以便进行调试的帮助器](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)描述不仅注册表位置需注册的调试引擎中; 它还介绍了 dbgmetric.lib 库，其中包含大量有用的函数和 c + + 开发人员所做的声明操作更容易注册表。  
  
### <a name="example"></a>示例  
 以下是用于演示如何使用的典型示例 （摘自 TextInterpreter 的示例）`SetMetric`函数 （从 dbgmetric.lib)，来注册 Visual Studio 的调试引擎。 传递的度量值也是在 dbgmetric.lib 中定义的。  
  
> [!NOTE]
>  TextInterpreter 是基本的调试引擎;它未实现，并因此不会注册-任何其他功能。 更完整的调试引擎都的整个列表`SetMetric`调用或其等效项，一个用于每个功能的调试引擎支持。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [SDK 适用于调试的帮助程序](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [教程： 构建使用 ATL COM 调试引擎](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)