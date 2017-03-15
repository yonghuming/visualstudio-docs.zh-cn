---
title: "&lt;deprecated&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定一个已弃用函数或方法。  
  
## 语法  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### 参数  
 `type`  
 可选。  指定函数或方法是否会在未来版本中移除，或者该函数或方法是否已经被移除，它的使用会导致错误。  设置`deprecate` 指定函数或方法将会在未来版本中被移除。  设置`remove` 指定函数或方法已经被移除。  
  
 `locid`  
 可选。  这个标示符是有关函数或方法的本地化信息。  该标识符是成员编号或它对应于OpenAjax元数据定义在消息绑定的 `name` 属性值。  这个标示符依赖在 [\<loc\>](../ide/loc-javascript.md) 元素中的指定形式。  
  
 `description`  
 可选。  已弃用函数或方法的说明。  
  
## 备注  
 这个元素用于标注函数，包括 `<deprecated>`，必须放在任何语句前面的函数体内。  当你把一个函数标记为已弃用,我们建议你将[\<summary\>](../ide/summary-javascript.md)元素替换为 `<deprecated>`元素。  
  
## 示例  
 下面的代码演示如何使用 `<deprecated>` 元素。  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## 请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)