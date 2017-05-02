---
title: "getVarDate 方法 (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "getVarDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 对象"
  - "getVarDate 方法"
  - "日期，VT_DATE 格式"
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# getVarDate 方法 (Date) (JavaScript)
从 `Date` 对象返回 VT\_DATE 值。  
  
> [!WARNING]
>  只有 Internet Explorer 支持此方法。  
  
## 语法  
  
```  
  
dateObj.getVarDate()   
```  
  
#### 参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回 VT\_DATE 值。  
  
## 备注  
 JavaScript 代码与 COM 对象、ActiveX 对象或其他可接收和返回 VT\_DATE 格式日期值的对象交互时，使用 `getVarDate` 方法。 其中包括 Visual Basic 和 Visual Basic Scripting Edition \(VBScript\) 中的对象。 返回值的实际格式取决于区域设置。  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。 请参阅[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse 函数](../../javascript/reference/date-parse-function-javascript.md)