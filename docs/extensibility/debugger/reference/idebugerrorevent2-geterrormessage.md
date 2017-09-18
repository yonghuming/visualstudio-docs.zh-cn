---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回允许一个可读的错误消息构造的信息。  
  
## 语法  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### 参数  
 `pMessageType`  
 \[out\] 返回从 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 枚举的值，描述的消息类型。  
  
 `pbstrErrorFormat`  
 \[out\] 最终消息的格式设置为用户 \(参见 “备注”有关详细信息\)。  
  
 `hrErrorReason`  
 \[out\] 错误消息的代码。  
  
 `pdwType`  
 \[out\] 错误的严重级别 \(对于 `MessageBox`请使用 MB\_XXX 常量;例如， `MB_EXCLAMATION` 或 `MB_WARNING`\)。  
  
 `pbstrHelpFileName`  
 \[out\] 帮助文件的路径 \(设置为空值，如果未帮助文件\)。  
  
 `pdwHelpId`  
 \[out\] 显示的帮助主题的 ID \(设置为 0; 如果没有帮助主题。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 应当沿 `"What I was doing.  %1"`行格式错误消息。  `"%1"` 将被调用方然后将替换为在 `hrErrorReason`返回\) 的错误代码派生的错误消息 \(。  `pMessageType` 参数告知调用方应如何显示最终错误消息。  
  
## 请参阅  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)