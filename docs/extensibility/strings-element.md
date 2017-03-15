---
title: "字符串元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 86e0148d495914b1cb1c0f0d19125992930a9521
ms.lasthandoff: 02/22/2017

---
# <a name="strings-element"></a>字符串元素
字符串元素必须包含至少一个**ButtonText**子元素。 所有其他子元素是可选的。 无效的 XML 字符，如 '.' 和 '<’ must="" be="" coded="" as="" entities=""></’>&amp;'和'&lt;，依此类推)。  
  
 And 符的文本字符串中指定该命令的键盘快捷方式。  
  
## <a name="syntax"></a>语法  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|语言|可选。 语言 ="。"。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|ButtonText|此字段和命令定义中的五个以下文本字段可以指定各种菜单中显示的文本。 默认情况下，`ButtonText`字段显示在菜单控制器中。 `ButtonText`字段也将成为默认如果其他文本字段为空白。 `ButtonText`字段不能为空白，即使指定了其他文本字段。|  
|ToolTipText|`ToolTipText`字段指定菜单项的工具提示中显示的文本。<br /><br /> 如果`ToolTipText`字段为空，`ButtonText`使用字段。|  
|MenuText|`MenuText`字段指定是否在主菜单上，在快捷菜单中，或作为子菜单中的工具栏上的命令显示的文本。 如果`MenuText`字段为空白，则在集成的开发环境 (IDE) 中使用`ButtonText`字段。 `MenuText`字段还用于本地化。<br /><br /> 对于快捷菜单，`MenuText`字段是显示在快捷菜单工具栏中，可以在 IDE 中的快捷菜单的自定义的名称。 因此，为特定中命名你的快捷菜单;例如，使用而不是"快捷方式"的"小组件的程序包快捷菜单"。<br /><br /> 如果`MenuText`未指定字段，`ButtonText`使用字段。|  
|CommandName|`CommandName`字段指定的键盘类别中显示的文本**命令**选项卡中**自定义**对话框 (可通过单击**自定义**上**工具**菜单)。|  
|CanonicalName|英语`CanonicalName`字段可以按输入的英语文本中指定的命令名称**命令**窗口来执行的菜单项。 IDE 将消除不是字母、 数字、 下划线或嵌入的期间的任何字符。 此文本然后串联成`ButtonText`字段来定义该命令。 例如，**新项目**上**文件**菜单将变成命令 File.NewProject。<br /><br /> 如果英语`CanonicalName`字段未指定，则 IDE 将使用`ButtonText`字段中，并带出全部除了字母、 数字、 下划线和嵌入的句点。 例如，按钮文本"< 定义命令..."将成为的 DefineCommands，删除与符号、 空格和省略号。<br /><br /> 如果`TextChanges`指定标志和命令的文本被更改，相应的命令被识别**命令**窗口不会更改; 它就一直与原始的规范格式`ButtonText`或英语`CanonicalName`字段。|  
|LocCanonicalName|`LocCanonicalName`字段的行为方式与英语相同`CanonicalName`字段，但可以本地化的命令文本才能指定。 可以指定这两个规范的字段。 因为 IDE 只需将分析输入中的文本**命令**窗口并将其与某个命令，英语和非英文文本可与相同的命令相关联的关联。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[Button 元素](../extensibility/button-element.md)|定义用户可以与交互元素。|  
|[Menu 元素](../extensibility/menu-element.md)|定义一个菜单项。|  
|[组合元素](../extensibility/combo-element.md)|定义在组合框中显示的命令。|  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
