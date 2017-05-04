---
title: "GetObject 函数 (JavaScript) | Microsoft Docs"
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
  - "GetObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetObject 函数"
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# GetObject 函数 (JavaScript)
从文件中返回对自动化对象的引用。  
  
> [!NOTE]
>  此函数在 Internet Explorer 9（标准模式）或更高版本中不受支持。  
  
## 语法  
  
```  
GetObject([pathname] [, class])  
```  
  
## 参数  
 `pathname`  
 可选。  包含要检索对象的文件的完整路径和名称。  如果省略了 `pathname`，则 `class` 为必选。  
  
 `class`  
 可选。  对象的类。  
  
 `class` 参数使用语法 `appname.objectype` 且包括以下部分：  
  
 `appname`  
 必需。  提供对象的应用程序的名称。  
  
 `objectype`  
 必需。  要创建的对象的类型或类。  
  
## 备注  
 `GetObject` 函数在 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 或更高版本中不受支持。  
  
 使用 `GetObject` 函数可以从文件中访问一个 Automation 对象。  可以将由 `GetObject` 返回的对象赋给对象变量。  例如：  
  
```javascript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 在执行此代码时，将启动与指定的 `pathname` 关联的应用程序，并将激活指定文件中的对象。  如果 `pathname` 是零长度字符串 \(""\)，则 `GetObject` 返回指定类型的新对象实例。  如果省略 `pathname` 参数，则 `GetObject` 返回指定类型的当前活动对象。  如果指定类型的对象不存在，则发生错误。  
  
 某些应用程序使您得以激活文件的部分内容。  若要实现此功能，请在文件名尾部加一个感叹号 \(\!\)，然后在感叹号后加一个用来标识要激活文件部分的字符串。  有关如何创建此字符串的信息，请参见创建对象的应用程序的文档。  
  
 例如，在绘图应用程序中可以使保存在文件中的绘图具有多个层。  可以使用以下代码激活名为 `SCHEMA.CAD` 的图形中的某一层：  
  
```javascript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 如果未指定对象的类，则自动化将根据所提供的文件名来确定要启动的应用程序和要激活的对象。  但是某些文件可能支持多个类的对象。  例如，一幅图形可能支持三种不同类型的对象：Application 对象、Drawing 对象和 Toolbar 对象，所有这些对象都是同一文件的组成部分。  若要指定要在文件中激活的对象，请使用可选 `class` 参数。  例如：  
  
```javascript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 在以上示例中，`FIGMENT` 是绘图应用程序的名称，而 `DRAWING` 是它支持的一种对象类型。  对象激活后，在代码中使用已定义的对象变量引用此对象。  在前面的示例中，可以使用对象变量 `MyObject` 访问新对象的属性和方法。  例如：  
  
```javascript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  如果存在对象的当前实例，或者您希望使用已加载的文件创建对象，请使用 `GetObject` 函数。  如果不存在当前实例，而且您也不希望使用已加载的文件来创建对象，则可以使用 `ActiveXObject` 对象。  
  
 如果对象本身已经注册为单实例对象，则无论执行多少次 `ActiveXObject`，也只创建一个对象实例。  对于单实例对象，当使用零长度字符串 \(""\) 语法调用时，`GetObject` 始终返回同一实例，如果省略 `pathname` 参数，则会导致错误。  
  
## 要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准、Internet Explorer 7 标准和 Internet Explorer 8 标准。  请参见 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
## 请参阅  
 [ActiveXObject 对象](../../javascript/reference/activexobject-object-javascript.md)