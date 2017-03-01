---
title: "IDebugProgramPublisher2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9251a24e1b52359a5c3f0810dced96cf69a3309b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
此接口允许调试引擎 (DE) 或自定义端口供应商进行注册以进行调试的程序。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 Visual Studio 实现此接口以注册以使它们以进行调试多个进程间可见正在调试的程序。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用 COM 的`CoCreateInstance`起作用`CLSID_ProgramPublisher`以获取此接口 （请参见示例）。 DE 或自定义端口供应商使用此接口来注册程序节点，表示正在调试的程序。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 此接口实现的以下方法︰  
  
|方法|说明|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|使程序节点可以为 DEs 和会话调试管理器 (SDM)。|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|移除程序节点，以便不再可用。|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|使程序可以为 DEs 和 SDM。|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|删除某个程序，以便不再可用。|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|设置一个标志，指示存在调试程序。|  
  
## <a name="remarks"></a>备注  
 此接口提供程序和程序节点 （即，"发布"它们） 以供 DEs 和会话调试管理器 (SDM)。 若要访问已发布的程序和程序节点，请使用[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)接口。 这是 Visual Studio 能够识别正在调试程序的唯一方法。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>示例  
 此示例演示如何实例化程序发行者和注册程序节点。 这从本教程中，获取[发布程序节点](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae)。  
  
```cpp#  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
