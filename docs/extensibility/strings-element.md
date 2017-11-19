---
title: "字符串元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea2f1808adcb7c8c79d2139e89e31f21a85cb694
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="strings-element"></a>字符串元素
字符串元素必须包含至少一个**ButtonText**子元素。 所有其他子元素是可选的。 无效的 XML 字符如 & 和 < 必须编码为实体 (&amp;和&lt;，依此类推)。  
  
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
  
|元素|描述|  
|-------------|-----------------|  
|ButtonText|此字段和命令定义中的五个以下文本字段让你指定各种菜单中显示的文本。 默认情况下，`ButtonText`字段显示在菜单控制器中。 `ButtonText`字段也成为默认的如果其他文本字段为空白。 `ButtonText`字段不能为空白，即使指定了其他文本字段。|  
|ToolTipText|`ToolTipText`字段指定菜单项的工具提示中显示的文本。<br /><br /> 如果`ToolTipText`字段为空白，`ButtonText`使用字段。|  
|MenuText|`MenuText`字段指定是否在主菜单中，工具栏上，在快捷菜单中，或在子菜单上显示命令的文本。 如果`MenuText`字段为空白，集成的开发环境 (IDE) 使用`ButtonText`字段。 `MenuText`字段还用于本地化。<br /><br /> 对于快捷菜单，`MenuText`字段是在快捷菜单工具栏中，允许自定义的快捷菜单在 IDE 中显示的名称。 因此，为特定中命名你的快捷菜单;例如，使用而不是"快捷方式"的"小组件的包快捷菜单"。<br /><br /> 如果`MenuText`未指定字段，`ButtonText`使用字段。|  
|CommandName|`CommandName`字段指定显示的文本的键盘类别中**命令**选项卡中**自定义**对话框 (通过单击可用**自定义**上**工具**菜单)。|  
|canonicalName|英语`CanonicalName`字段可输入的英语文本中指定的命令名称**命令**窗口执行菜单项。 IDE 将消除不是字母、 数字、 下划线或嵌入的期间的任何字符。 此文本然后连接到`ButtonText`字段来定义该命令。 例如，**新项目**上**文件**菜单将变成命令，File.NewProject。<br /><br /> 如果英语`CanonicalName`字段未指定，则 IDE 使用`ButtonText`字段和所有除字母、 数字、 下划线和嵌入的句点的条带。 例如，按钮文本"& 定义命令..."将成为的 DefineCommands，删除 & 符、 空间和旁边的省略号。<br /><br /> 如果`TextChanges`指定标志且命令的文本已更改，识别的相应命令**命令**窗口不会更改; 它会保持原始的规范格式`ButtonText`或英语`CanonicalName`字段。|  
|LocCanonicalName|`LocCanonicalName`字段的行为方式与英语相同`CanonicalName`字段，但可以指定的本地化的命令文本。 可以指定这两个规范的字段。 因为 IDE 只需将分析输入中的文本**命令**窗口并将其与某个命令，英语和非英语文本可以与同一命令相关联的关联。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Button 元素](../extensibility/button-element.md)|定义用户可以与交互元素。|  
|[Menu 元素](../extensibility/menu-element.md)|定义一个菜单项。|  
|[Combo 元素](../extensibility/combo-element.md)|定义在组合框中显示的命令。|  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)