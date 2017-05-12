---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
通知帮助器给定可用的文本，但是，它不提供字符。  
  
## 语法  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### 参数  
 `cChars`  
 \[in\] \(添加\)的Unicode字符数。  
  
 `dwTextStartCookie`  
 \[in\]表示该文本的起始位置的宿主中定义的cookie。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|失败的方法。|  
  
## 备注  
 此方法允许主机延迟提供字符添加，只在需要时才，则为;如果允许帮助器生成准确通知和范围信息时。  `dwTextStartCookie` 参数是cookie，定义宿主，表示该文本的起始位置。  以后对 `IDebugDocumentText::GetText` 必须提供此cookie。  例如，在表示在DBCS文本的主机，cookie可以为字节偏移量。  
  
 假定，唯一调用 `IDebugDocumentText::GetText` 可以从多个捕获字符对 `AddDeferredText`。  帮助器选件类可以多次还请求推迟字符的同一范围。  
  
> [!NOTE]
>  调用 `AddDeferredText` 不应组合通过调用 `AddUnicodeText` 或 `AddDBCSText`。  如果发生这种情况，`E_FAIL` 返回。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)