---
title: "JSON 对象 (JavaScript) | Microsoft Docs"
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
  - "JSON"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON 对象"
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# JSON 对象 (JavaScript)
一个内部对象，提供用于在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值和 JavaScript 对象表示法 \(JSON\) 格式之间来回转换的函数。  `JSON.stringify` 函数可将 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值序列化为 JSON 文本。  `JSON.parse` 函数可反序列化 JSON 文本以生成 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值。  
  
## 语法  
  
```  
  
JSON.[method]  
  
```  
  
## 参数  
 `Method`  
 必需。  `JSON` 对象的某一个方法的名称。  
  
## 备注  
 你无法使用 `new` 运算符创建 `JSON` 对象。  如果尝试执行此操作，则将出错。  但是，你可以重写或修改 `JSON` 对象。  
  
 加载脚本引擎时，该引擎将创建 `JSON` 对象。  其方法始终对你的脚本可用。  
  
 若要使用内部 `JSON` 对象，请确保不使用脚本中定义的另一个 `JSON` 对象来重写该对象。  你可能需要修改将检测 `JSON` 对象的状态的现有脚本语句，因为这些语句将以不同的方式计算。  下面的示例说明了这一点。  
  
```javascript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 在前面的示例中，`!this.JSON` 的计算结果在 [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)]中为 false。  因此，`if` 语句中的代码将不执行。  
  
## 函数  
 [JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)  
  
 [JSON.stringify 函数](../../javascript/reference/json-stringify-function-javascript.md)  
  
## 要求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## 请参阅  
 [toJSON 方法 \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [JavaScript 对象](../../javascript/reference/javascript-objects.md)   
 [中心模板示例应用（Windows 应用商店）](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)