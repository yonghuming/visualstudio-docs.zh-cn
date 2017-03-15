---
title: "如何：创建 JavaScript XML 文档注释 | Microsoft Docs"
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
  - "代码注释, JavaScript IntelliSense"
  - "文档注释 [JavaScript]"
  - "IntelliSense [JavaScript], XML 文档注释"
  - "XML 文档注释, JavaScript IntelliSense"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：创建 JavaScript XML 文档注释
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*XML 文档注释*是 JavaScript 注释添加到脚本提供有关代码元素 （如函数、 字段和变量的信息。  在 Visual Studio，这些文本说明显示与 IntelliSense 时，引用的脚本函数。  
  
 本主题提供基本教程，说明如何使用 XML 文档注释。  有关使用其他元素，如[\<var\>](../ide/var-javascript.md)和[\<value\>](../ide/value-javascript.md)，和其他代码示例，请参阅[XML 文档注释](../ide/xml-documentation-comments-javascript.md)。  有关提供 IntelliSense 的异步回调的信息，如`Promise`，请参阅[\<returns\>](../ide/returns-javascript.md)。  
  
> [!NOTE]
>  只能从引用的文件、 程序集和服务可用 XML 文档注释。  
  
### 若要创建 XML 文档注释的 JavaScript 函数  
  
-   在函数中，添加[\<summary\>](../ide/summary-javascript.md)， [\<param\>](../ide/param-javascript.md)，和[\<returns\>](../ide/returns-javascript.md)元素，并在前面三个斜杠 \(\/ \/\) 与每个元素。  
  
    > [!NOTE]
    >  每个元素必须全部在一行上。  
  
     下面的示例演示一个 JavaScript 函数。  
  
    ```javascript  
    function getArea(radius)  
    {  
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>  
        /// <param name="radius" type="Number">The radius of the circle.</param>  
        /// <returns type="Number">The area.</returns>  
        var areaVal;  
        areaVal = Math.PI * radius * radius;  
        return areaVal;  
    }  
    ```  
  
-   要查看 XML 文档注释，请键入名称和左括号的函数，如下例所示的 XML 文档注释标记：  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     在键入左括号的函数包含 XML 文档注释的时，代码编辑器中使用 IntelliSense 显示 XML 文档注释中定义的信息。  
  
### 若要创建 JavaScript 字段的 XML 文档注释  
  
-   在构造函数的函数或对象定义中添加[\<field\>](../ide/field-javascript.md)元素前面三个斜杠 \(\/ \/\)。  
  
     下面的示例显示如何使用`<field>`构造函数中的元素。  有关其他示例，请参见[\<field\>](../ide/field-javascript.md)。  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   若要查看 XML 文档注释，请通过使用 XML 文档注释，如下例所示使用函数构造函数标记为创建对象。  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   在下一行中，键入该对象，以显示该字段的 IntelliSense 信息段的名称。  
  
    ```javascript  
    eng.  
    ```  
  
### 若要创建 XML 文档注释的重载函数  
  
1.  在函数中，添加[\<signature\>](../Topic/%3Csignature%3E%20\(JavaScript\).md)元素，为每个重载。  在这些元素中，添加其他元素，如`<summary>`， `<param>`，和`<returns>`前三个斜杠 \(\/ \/\) 与每个元素。  
  
     下面的示例演示重载的 JavaScript 函数。  在此示例中，参数类型不同的重载。  
  
    ```javascript  
    function calc(a) {  
        /// <signature>  
        /// <summary>Function summary 1.</summary>  
        /// <param name="a" type="Number">A number.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        /// <signature>  
        /// <summary>Function summary 2.</summary>  
        /// <param name="a" type="String">A string.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        return a;  
    }  
    ```  
  
2.  要查看 XML 文档注释，请键入名称和左括号的函数的使用，如下例所示的 XML 文档注释标记：  
  
    ```javascript  
    calc(  
    ```  
  
### 若要创建本地化的 IntelliSense  
  
1.  创建具有 OpenAjax MessageBundle 格式的文档注释的 XML 文件。  
  
    > [!IMPORTANT]
    >  MessageBundle 是推荐的格式。  在 Microsoft Ajax 或.winmd 文件中不支持此格式。  有关使用另一种`VSDoc`设置的格式，请参阅[\<loc\>](../ide/loc-javascript.md)。  
  
     下面的示例中包含本地化的 IntelliSense 信息的附属文件的显示内容。  这是一个 XML 文件，它位于一个特定于区域性的文件夹，如 JA。  该文件夹必须为.js 文件所在的相同位置中`<loc>`元素。  XML 文件的文件名必须与匹配`filename`参数中指定`<loc>`元素。  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  在.js 文件中，添加以下代码。  `<loc>`元素，必须声明之前的任何脚本，并遵循相同的用法规则`<reference>`元素。  有关更多信息，请参见[JavaScript IntelliSense](../ide/javascript-intellisense.md)和 [\<loc\>](../ide/loc-javascript.md)。  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  在.js 文件中，添加的 XML 文档的元素和默认说明。  设置`locid`属性值，以匹配相应的`name`从附属文件属性值。  如果可用本地化的 IntelliSense 信息将被替换的默认说明。  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  要查看 XML 文档注释，请键入名称和左括号的函数，如下例所示：  
  
    ```javascript  
    add(  
    ```  
  
## 请参阅  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/zh-cn/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)