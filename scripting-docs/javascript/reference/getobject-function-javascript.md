---
title: "GetObject 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getobject-function-javascript"></a>GetObject 函数 (JavaScript)
返回对自动化对象从文件的引用。  
  
> [!NOTE]
>  此函数不支持在 Internet Explorer 9 （标准模式） 或更高版本。  
  
## <a name="syntax"></a>语法  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>参数  
 `pathname`  
 可选。 完整路径和包含要检索的对象的文件的名称。 如果`pathname`省略，`class`是必需的。  
  
 `class`  
 可选。 对象的类。  
  
 `class`自变量使用语法`appname.objectype`和分为三个部分：  
  
 `appname`  
 必需。 提供对象的应用程序的名称。  
  
 `objectype`  
 必需。 若要创建的类型或类的对象。  
  
## <a name="remarks"></a>备注  
 `GetObject`中不支持函数[!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]或更高版本。  
  
 使用`GetObject`函数从文件访问的自动化对象。 将返回的对象分配`GetObject`给对象变量。 例如：  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 执行此代码时，使用指定关联的应用程序`pathname`已启动，并且指定的文件中的对象将被激活。 如果`pathname`是零长度字符串 ("")，`GetObject`返回指定类型的新对象实例。 如果`pathname`省略参数，则`GetObject`返回指定类型的当前处于活动状态对象。 如果不存在的对象指定的类型，就会出错。  
  
 某些应用程序，可以激活文件的一部分。 为此，请将感叹号 （！） 添加到的文件名称的末尾，并在其后加一个字符串，标识你想要激活的文件的一部分。 有关如何创建此字符串的信息，请参阅创建对象的应用程序的文档。  
  
 例如，一个绘图应用程序中可能有存储在文件中的图形的多个层。 你可以使用以下代码来激活调用`SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 如果未指定对象的类，则自动化功能会根据你提供的文件名自动确定要启动的应用程序和要激活，哪些对象。 但是，某些文件可能支持对象的多个的类。 例如，绘图可能支持三种不同类型的对象： 应用程序对象、 图形对象和工具栏对象，这些全部都是相同的文件的一部分。 若要指定想要激活的对象文件中，使用可选`class`自变量。 例如：  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 在前面的示例中，`FIGMENT`是一个绘图应用程序的名称和`DRAWING`是它支持的对象类型之一。 一旦激活一个对象，您可以在代码中使用所定义的对象变量引用它。 在前面的示例中，你可以访问使用对象变量的新对象的属性和方法`MyObject`。 例如：  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  使用`GetObject`函数时的当前实例的对象，或如果你想要创建的对象已加载的文件。 如果没有当前实例，并且你不希望开始使用的对象加载的文件，请使用`ActiveXObject`对象。  
  
 如果对象已将自己注册为单实例对象，该对象的一个实例创建了，无论多次`ActiveXObject`执行。 对于单实例对象，`GetObject`始终返回同一个实例时调用的零长度字符串 ("") 语法，并导致的错误，如果`pathname`忽略自变量。  
  
## <a name="requirements"></a>要求  
 在以下文档模式中受支持： Quirks、 Internet Explorer 6 标准、 Internet Explorer 7 标准和 Internet Explorer 8 标准。 请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
## <a name="see-also"></a>另请参阅  
 [ActiveXObject 对象](../../javascript/reference/activexobject-object-javascript.md)