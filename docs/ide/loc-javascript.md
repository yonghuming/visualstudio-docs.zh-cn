---
title: "&lt;loc&gt; (JavaScript) | Microsoft Docs"
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
  - "<loc> JavaScript XML 标记"
  - "loc JavaScript XML 标记"
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定提供本地化 IntelliSense 信息的附属文件的位置和类型。  
  
## 语法  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### 参数  
 `filename`  
 可选。  包含本地化信息的中性文化的附属文件的根名称。  当在 Visual Studio 中搜索特定本地化信息时，它尝试查找该文件的一个特定区域性版本。  例如，如果 `filename` 是jquery.xml，在和包含 `<loc>` 元素的 .js 文件一样的位置，Visual Studio搜索正确的区域性特定文件夹（如JA）。  如果它找到该特定于区域性的文件夹，它检查 jquery.xml 文件是否存在于它。  如果它不能定位到正确的文件，它使用托管资源位置规则。  `filename` 默认值为当前文件的名称，但是具有 .xml 文件扩展名而不是 .js。  
  
 `format`  
 可选。  用于本地化的附属文件的类型。  使用 `messagebundle` 指定使用消息束通过开放式的Ajax元数据定义。  `messagebundle` 是推荐的格式。  然而，这种格式在微软的 Ajax 或 .winmd 文件不支持。  使用 `vsdoc` 指定的标准，是由 Microsoft Ajax 和 Windows 运行时 .NET 框架的本地化格式。  此特性是可选的。  默认格式为 `vsdoc`。  
  
## 备注  
 `<loc>` 元素必须出现在和 `<reference>` 元素同意区域的文件的顶部。  `<loc>` 元素的使用情况规则和`<reference>` 元素一样。  有关更多信息，请参见 [JavaScript IntelliSense](../ide/javascript-intellisense.md) 中的“引用指示”部分。  
  
 Visual Studio 处理每个 .js 文件的单独的 `<loc>` 元素。  如果多个 `<loc>` 元素存在，只有 `<loc>` 元素有用。  行为决定哪些 `<loc>` 元素使用没有定义。  
  
 当使用消息束格式，请使用 `locid` 在XML文档的属性来注释来指定 `name` 属性值。  
  
## 示例  
 下面的示例演示如何将 `<loc>` 元素和信息束格式结合使用。  将以下XML添加到一个名为messageFilename.xml文件，并将该文件放在正确的区域性特定的文件夹，如 `filename` 参数的描述中指定。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 对于 messagebundle 示例，请将以下代码添加到您的项目中的 JavaScript 文件。  `<loc>` 元素必须在 JavaScript 文件的第一行。  如果有的话，在这段代码中的描述将被本地化的说明代替。  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 下面的示例使用 VSDoc 格式。  将以下XML添加到一个名为scriptFilename.xml文件，并将该文件放到正确的区域性特定的文件夹。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 对于 VSdos 示例，请将以下代码添加到您的项目中的 JavaScript 文件。  如果有的话，在这段代码中的描述将被本地化的说明代替。  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## 请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)