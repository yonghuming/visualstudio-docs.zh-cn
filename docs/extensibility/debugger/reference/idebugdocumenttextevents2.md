---
title: "IDebugDocumentTextEvents2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 242c15cc456c3a27ba7b7da45a11031b026c02d3
ms.lasthandoff: 04/05/2017

---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
使用此接口来通知 Visual Studio 的调试引擎提供对源文档的更改。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 DE 实现此接口以支持对源代码进行更改。 实现对同一个对象通常实现此接口[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]获取通过调用此接口<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法。</xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>接口从调用中获取<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>方法。</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>接口通过调用获取[QueryInterface](/cpp/atl/queryinterface)方法[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)接口。</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugDocumentTextEvents2`。  
  
|方法|描述|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|指示整个文档已被破坏。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|通知调试包文本已插入到文档。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|通知已从文档中删除文本调试包。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|通知已替换文本为文档中调试包。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|通知文本特性具有已更新文档中调试包。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|通知的事件的接收方已更新的文档属性。|  
  
## <a name="remarks"></a>备注  
 仅提供自己的文档的调试引擎将利用`IDebugDocumentTextEvent2`接口。 此示例将脚本的调试引擎。 过程中解释脚本，新的源代码可以生成不存在任何磁盘文件中，仅对 DE 已知。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
