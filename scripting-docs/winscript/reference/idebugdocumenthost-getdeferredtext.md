---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
使用 `IDebugDocumentHelper::AddDeferredText` 方法，它返回添加字符的范围，原始宿主文档。  
  
## 语法  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### 参数  
 `dwTextStartCookie`  
 \[in\]表示该文本的起始位置的宿主中定义的cookie。  
  
 `pcharText`  
 \[in，out\] A字符文本缓冲区。  如果此参数是 `NULL`，此方法不返回字符。  
  
 `pstaTextAttr`  
 \[in，out\] A字符缓冲区属性。  如果此参数是 `NULL`，此方法不返回属性。  
  
 `pcNumChars`  
 \[in，out\]指示返回的字符\/属性的实际数目。  必须将此参数设置为在调用此方法之前为零。  
  
 `cMaxChars`  
 \[in\]返回的最大字符数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|此方法未实现。|  
  
## 备注  
 如果宿主不调用 `IDebugDocumentHelper::AddDeferredText`，此方法会返回 `E_NOTIMPL`。  
  
> [!NOTE]
>  此方法返回从原的文本文件。  宿主不编辑记录或指向文档的其他更改。  
  
## 请参阅  
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)