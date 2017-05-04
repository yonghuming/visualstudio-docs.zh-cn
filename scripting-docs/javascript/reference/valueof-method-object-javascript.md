---
title: "valueOf 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf 方法"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# valueOf 方法 (Object) (JavaScript)
返回指定对象的基元值。  
  
## 语法  
  
```  
  
object.valueOf( )  
```  
  
## 备注  
 必需的 `object` 引用是任何内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象。  
  
 将通过不同的方式为每个内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象定义 `valueOf` 方法。  
  
|对象|返回值|  
|--------|---------|  
|数组|返回数组实例。|  
|布尔值|布尔值。|  
|日期|从 UTC 1970 年 1 月 1 日午夜开始的存储的时间值（以毫秒为单位）。|  
|函数|函数本身。|  
|Number|数字值。|  
|对象|对象本身。  这是默认值。|  
|字符串|字符串值。|  
  
 **Math** 和 `Error` 对象都没有 `valueOf` 方法。  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **适用于**：[Array 对象](../../javascript/reference/array-object-javascript.md)&#124; [Boolean 对象](../../javascript/reference/boolean-object-javascript.md)&#124; [Date 对象](../../javascript/reference/date-object-javascript.md)&#124; [Function 对象](../../javascript/reference/function-object-javascript.md)&#124; [Number 对象](../../javascript/reference/number-object-javascript.md)&#124; [Object 对象](../../javascript/reference/object-object-javascript.md)&#124; [String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [toString 方法 \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)