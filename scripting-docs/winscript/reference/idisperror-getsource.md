---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
返回引发此错误的选件类或应用程序的相关语言的编程标识符。  
  
## 语法  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### 参数  
 `pbstrSource`  
 \[in\]请字符串包含的编程标识符，在窗体 `progname.objectname`。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法用于确定发生异常的选件类或应用程序。  该编程标识符在区域设置标识符指定的语言可能返回在调用过程中提供的\(LCID\)。  
  
> [!NOTE]
>  此方法未实现。  
  
## 请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)