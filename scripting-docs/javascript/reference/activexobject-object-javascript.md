---
title: "ActiveXObject 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ActiveXObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ActiveXObject object
- Automation objects, ActiveXObject objects
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77bb743aeab563f7d7711e4caa9a0fcf0b45ff58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="activexobject-object-javascript"></a>ActiveXObject 对象 (JavaScript)
启用和返回对自动化对象的引用。  
  
 此对象仅用于实例化自动化对象，且此对象没有成员。  
  
> [!WARNING]
>  此对象为 Microsoft 扩展，仅在 Internet Explorer 中受支持，在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。  
  
## <a name="syntax"></a>语法  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## <a name="parameters"></a>参数  
 `newObj`  
 必需。 `ActiveXObject` 分配到的变量名称。  
  
 `servername`  
 必需。 提供对象的应用程序的名称。  
  
 `typename`  
 必需。 要创建的对象的类型或类。  
  
 `location`  
 可选。 要在其中创建对象的网络服务器的名称。  
  
## <a name="remarks"></a>备注  
 自动化服务器至少提供一种对象。 例如，字处理应用程序可能会提供应用程序对象、文档对象和工具栏对象。  
  
 你可以在 `servername.typename` 注册表项中标识宿主 PC 上的 `HKEY_CLASSES_ROOT` 值。 例如，下面是可在此处找到的几个值示例，具体取决于安装的程序：  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  ActiveX 对象可能存在安全问题。 若要使用 `ActiveXObject`，你可能需要在相关安全区域的 Internet Explorer 中调整安全设置。 例如，对于本地 Intranet 区域，通常需要将自定义设置更改为“对没有标记为安全的 ActiveX 控件进行初始化和脚本运行”。  
  
 若要标识可以在代码中使用自动化对象的成员，你可能需要使用 COM 对象浏览器中，如[OLE/COM 对象查看器](http://msdn.microsoft.com/library/d0kh9f4c.aspx)，如果没有参考文档都是可用于自动化对象。  
  
 若要创建自动化对象，请将新的 `ActiveXObject` 分配给对象变量：  
  
```JavaScript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 此代码启动创建对象的应用程序（在此示例中，为 Microsoft Excel 工作表）。 在创建某个对象后，可在代码中使用已定义的对象变量引用该对象。 在下面的示例中，使用对象变量 `ExcelSheet` 和其他 Excel 对象（包括应用程序对象和 ActiveSheet.Cells 集合）来访问新对象的属性和方法。  
  
```JavaScript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## <a name="requirements"></a>要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式、Internet Explorer 10 标准模式和 Internet Explorer 11 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。 请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
> [!NOTE]
>  `ActiveXObject`或更高版本不支持在远程服务器上创建 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [GetObject 函数](../../javascript/reference/getobject-function-javascript.md)   
 [使用 HTML5/WCF 幻示例应用程序的唯一身份验证](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)