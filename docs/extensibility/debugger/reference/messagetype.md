---
title: "MESSAGETYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MESSAGETYPE
helpviewer_keywords: MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7cbb3ddd27c7cbb92c7e248c5091d6fe0e21dc3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="messagetype"></a>MESSAGETYPE
指定的消息类型和原因。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>成员  
 MT_OUTPUTSTRING  
 指示应将消息发送到输出窗口。 这是从互斥`MT_MESSAGEBOX`。  
  
 MT_MESSAGEBOX  
 指示应在消息框中显示消息。 这是从互斥`MT_OUTPUTSTRING`。  
  
 MT_TYPE_MASK  
 若要隔离消息目标掩码值。  
  
 MT_REASON_EXCEPTION  
 指示由于异常，正在显示一个消息框。 这是从互斥`MT_REASON_TRACEPOINT`。  
  
 MT_REASON_TRACEPOINT  
 指示已被一个消息框显示由于命中跟踪点。 这是互相排斥`MT_REASON_EXCEPTION`。  
  
 MT_REASON_MASK  
 若要隔离正在显示的消息的原因掩码值。  
  
## <a name="remarks"></a>备注  
 这些值返回从[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)和[GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)方法。  
  
 其中一个原因值可以与一个输出目标值按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)