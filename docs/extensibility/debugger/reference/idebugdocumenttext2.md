---
title: "IDebugDocumentText2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2
helpviewer_keywords: IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebcb90f570ad29f38eabe8712928b484fd6961c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
此接口表示一个文本文档。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口，它需要提供的源代码时以文本形式。 由于这是最典型的情况下，如果 DE 实现[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)接口，它还应实现`IDebugDocumentText2`接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 使用`QueryInterface`方法来获取此接口从`IDebugDocument2`接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了上的方法`IDebugDocument2`接口，此接口实现以下方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|检索在此位置上的文档中的文本的大小。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|从文档中的指定位置检索文本。|  
  
## <a name="remarks"></a>备注  
 实现此接口的对象，还必须实现<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>接口，哪些提供<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>接口[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)对象。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)