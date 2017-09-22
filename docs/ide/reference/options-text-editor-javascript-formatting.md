---
title: "“选项”->“文本编辑器”->“JavaScript”->“格式设置”| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1791b8ae5877b007772224b359c836e7a0804f5c
ms.contentlocale: zh-cn
ms.lasthandoff: 02/22/2017

---
# <a name="options-text-editor-javascript-formatting"></a>Options, Text Editor, JavaScript, Formatting
使用“选项”对话框的“格式设置”页在代码编辑器中设置用于代码格式设置的选项。 若要访问此页，请在菜单栏上选择“工具”、“选项”，然后依次展开“文本编辑器”、“JavaScript”和“格式设置”。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="automatic-formatting"></a>自动格式设置  
 这些选项可确定在“源”视图中设置格式的时间。  
  
## <a name="uielement-list"></a>UIElement 列表  
  
|选项|描述|  
|------------|-----------------|  
|**按 Enter 时设置已完成行的格式**|选择此选项后，如果按 Enter 键，代码编辑器会自动设置该行的格式。|  
|**输入 ; 时设置已完成语句的格式**|选择此选项后，如果按分号键，代码编辑器会自动设置该行的格式。|  
|**输入 } 时设置已完成块的格式**|选择此选项后，如果按右大括号键，代码编辑器会自动设置该行的格式。|  
|**粘贴时设置格式**|选择此选项后，如果将代码粘贴到编辑器中，代码编辑器会重新设置该代码的格式。 编辑器使用当前定义的格式设置规则。 如未选择此选项，则编辑器使用粘贴代码的原始格式设置。|  
  
## <a name="new-lines"></a>新行  
 这些选项可确定代码编辑器是否将函数和控制块的左大括号置于新行。  
  
## <a name="uielement-list"></a>UIElement 列表  
  
|选项|描述|  
|------------|-----------------|  
|**将函数的左大括号置于新行**|选择此选项后，代码编辑器会将与函数关联的左大括号移动到新行。|  
|**将控制块的左大括号置于新行**|选择此选项后，代码编辑器会将与控制块（例如，`if` 和 `while` 控制块）关联的左大括号移动到新行。|  
  
## <a name="spacing"></a>间距  
 这些选项可确定在“源”视图中插入空格的方式。  
  
## <a name="uielement-list"></a>UIElement 列表  
  
|选项|说明|  
|------------|-----------------|  
|**在逗号分隔符后插入空格**|选择此选项后，代码编辑器会在逗号分隔符后添加空格。|  
|**在“for”语句中的分号后插入空格**|选择此选项后，代码编辑器会在 `for` 循环首行的每个分号后添加一个空格。|  
|**在二元运算符前后插入空格**|选择此选项后，代码编辑器会在二元运算符（例如，+、-、&&、||）前后各添加一个空格。|  
|**在控制流语句中的关键字后面插入空格**|选择此选项后，代码编辑器会在控制流语句中的 JavaScript 关键字后添加一个空格。|  
|**在匿名函数的函数关键字后插入空格**|选择此选项后，代码编辑器会匿名函数的 `function` 关键字后添加一个空格。|  
|**在非空左括号之后和非空右括号之前插入空格**|选择此选项后，如果括号内存在非空字符，代码编辑器会在左括号之后和右括号之前添加一个空格。|  
  
## <a name="see-also"></a>另请参阅  
 [“选项”对话框 ->“环境”->“常规”](../../ide/reference/general-environment-options-dialog-box.md)
