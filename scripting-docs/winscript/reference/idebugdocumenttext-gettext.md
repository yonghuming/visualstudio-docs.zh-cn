---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
检索字符和字符的属性与字符位置范围。  
  
## 语法  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### 参数  
 `cCharacterPosition`  
 \[in\]启动字符位置范围的位置。  
  
 `pcharText`  
 \[in，out\] A字符文本缓冲区。  缓冲区绑定足以容纳 `cMaxChars` 字符。  如果此参数是NULL，方法不返回字符。  
  
 `pstaTextAttr`  
 \[in，out\] A字符缓冲区属性。  缓冲区绑定足以容纳 `cMaxChars` 字符。  如果此参数是NULL，方法不返回属性。  
  
 `pcNumChars`  
 \[in，out\]字符\/属性数返回。  必须将此参数设置为在调用此方法之前为零。  
  
 `cMaxChars`  
 \[in\]中的字符数。字符位置的大小。  并指定的最大字符数返回。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法检索字符和\/或字符的属性与字符位置排列。  字符位置范围由字符位置与大量字符指定。  
  
## 请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE\_TEXT\_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)