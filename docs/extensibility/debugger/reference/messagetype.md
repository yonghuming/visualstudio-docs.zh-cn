---
title: "MESSAGETYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MESSAGETYPE"
helpviewer_keywords: 
  - "MESSAGETYPE 枚举"
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MESSAGETYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定消息类型及其原因。  
  
## 语法  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```c#  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## 成员  
 MT\_OUTPUTSTRING  
 指示应将消息发送到输出窗口。  这将从 `MT_MESSAGEBOX`是互斥的。  
  
 MT\_MESSAGEBOX  
 指示在消息框中显示消息。  这将从 `MT_OUTPUTSTRING`是互斥的。  
  
 MT\_TYPE\_MASK  
 隔离消息的目标的掩码值。  
  
 MT\_REASON\_EXCEPTION  
 指示由于异常，消息框显示。  这将从 `MT_REASON_TRACEPOINT`是互斥的。  
  
 MT\_REASON\_TRACEPOINT  
 指示由于命中跟踪点，消息框显示。  这是互斥到 `MT_REASON_EXCEPTION`。  
  
 MT\_REASON\_MASK  
 隔离显示的消息的原因的掩码值。  
  
## 备注  
 这些值是通过 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) 和 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) 方法返回。  
  
 使用 `OR`，其中一个原因值可以按位组合使用一个输出目标值。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)