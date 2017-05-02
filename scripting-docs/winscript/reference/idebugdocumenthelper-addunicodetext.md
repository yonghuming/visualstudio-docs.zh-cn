---
title: "IDebugDocumentHelper::AddUnicodeText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddUnicodeText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddUnicodeText"
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddUnicodeText
追加Unicode字符串到此端的文档。  
  
## 语法  
  
```  
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### 参数  
 `pszText`  
 \[out\]一个指向包含文本的一个Null结尾的字符串的指针。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法无法添加字符。|  
  
## 备注  
 此方法生成 `IDebugDocumentTextEvents` 通知。  
  
> [!NOTE]
>  如果调用此方法，在 `AddDeferredText` 调用之后，`E_FAIL` 返回。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents 接口](../../winscript/reference/idebugdocumenttextevents-interface.md)