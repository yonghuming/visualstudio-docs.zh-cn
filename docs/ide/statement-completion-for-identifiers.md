---
title: "适用于标识符的语句结束 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [JavaScript], 语句结束"
  - "语句结束, JavaScript IntelliSense"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 适用于标识符的语句结束
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript 不允许显式变量声明用于键入。  因此，IntelliSense 始终不能提供完成列表的对象。  这可能会在各种情况下。  以下是一些常见的原因。  
  
-   声明一个参数，但它尚未调用其他地方在活动文档中，如下面的示例中所示。  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   对象是在响应事件时调用的函数中。  在设计时，IntelliSense 引擎无法确定这种情况下使用的对象的类型。  
  
     如果 IntelliSense 引擎可以确定该事件应调用，通常通过使用`addEventListener`在活动文档中的事件，提供了更准确的 IntelliSense 信息。  
  
 IntelliSense 无法识别的对象时，IntelliSense 引擎完成使用填充列表命名的实体或存在于活动文档中的标识符。  完成列表中包含这些标识符，它们旁边将显示信息图标。  此外，为每个标识符的工具提示指示表达式是未知的。  下面的插图显示语句完成选项类型的对象的`light`是未定义的对象，而且其属性，因为无法识别的。  但是， `intensity`标识符列表中的可用属性是因为它已在使用`illuminate`函数。  
  
 **无法识别的对象完成选项**  
  
 ![适用于标识符的 JavaScript IntelliSense](~/ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 您可以通过使用 XML 文档注释或 JavaScript IntelliSense 的扩展性功能覆盖对象的完成列表。  使用这些功能，您可以提供类型信息和更具描述性的 IntelliSense 信息时它可能否则不可用。  有关更多信息，请参见[扩展 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)和 [如何：创建 JavaScript XML 文档注释](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)。  
  
## 请参阅  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)