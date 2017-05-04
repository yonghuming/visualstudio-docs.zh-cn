---
title: "Enumerator 对象 (JavaScript) | Microsoft Docs"
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
  - "Enumerator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Enumerator 对象"
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Enumerator 对象 (JavaScript)
支持集合中项目的枚举。  
  
> [!WARNING]
>  此对象仅在 Internet Explorer 中受支持，在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。  
  
## 语法  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## 参数  
 `enumObj`  
 必需。`Enumerator` 对象分配到的变量名称。  
  
 `collection`  
 可选。 任何集合对象。  
  
## 备注  
 集合与数组不同，不能直接访问集合的成员。 可在数组中使用索引，但在集合中，只能将当前项指针移动到第一个或下一个元素。  
  
 `Enumerator` 对象提供可用于访问集合中任意成员的方法，其行为方式类似于 VBScript 中的 `For...Each` 语句。  
  
## 示例  
 下面的代码将演示 `Enumerator` 对象的用法：  
  
```javascript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## 属性  
 `Enumerator` 对象没有属性。  
  
## 方法  
 [atEnd 方法](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [item 方法](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [moveFirst 方法](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [moveNext 方法](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。 请参阅[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
## 请参阅  
 [Boolean 对象](../../javascript/reference/boolean-object-javascript.md)