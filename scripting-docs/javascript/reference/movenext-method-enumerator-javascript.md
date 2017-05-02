---
title: "moveNext 方法 (Enumerator) (JavaScript) | Microsoft Docs"
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
  - "moveNext"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "MoveNext 方法"
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# moveNext 方法 (Enumerator) (JavaScript)
将当前项移动到集合中的下一项。  
  
> [!WARNING]
>  此对象仅在 Internet Explorer 中受支持。  
  
## 语法  
  
```  
  
enumObj.moveNext( )   
```  
  
## 备注  
 所需 *enumObj* 引用可以是任何 `Enumerator` 对象。  
  
 如果枚举器位于集合的末尾或集合为空，则将当前行设置为未定义。  
  
## 示例  
 在以下示例中，使用 **moveNext** 方法移动到 `Drives` 集合中下一个驱动器：  
  
```javascript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。 请参阅[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**：[Enumerator 对象](../../javascript/reference/enumerator-object-javascript.md)  
  
## 请参阅  
 [atEnd 方法 \(Enumerator\)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [item 方法 \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst 方法 \(Enumerator\)](../../javascript/reference/movefirst-method-enumerator-javascript.md)