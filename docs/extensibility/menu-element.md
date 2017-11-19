---
title: "Menu 元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4a0aa02b3375a7b5d66d26e11dcedbd7b67d958
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="menu-element"></a>Menu 元素
定义一个菜单项。 下面列出了六种菜单： 上下文、 菜单、 MenuController、 MenuControllerLatched、 工具栏上，和 ToolWindowToolbar。  
  
## <a name="syntax"></a>语法  
  
```  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。 GUID/ID 命令标识符的 GUID。|  
|id|必需。 ID 的 GUID/ID 命令标识符。|  
|priority|可选。 一个数字值，指定组中的菜单的菜单的相对位置。|  
|ToolbarPriorityInBand|可选。 停靠窗口以一个带指定工具栏的相对位置的数字值。|  
|类型|可选。 一个枚举的值，指定的元素的类型。<br /><br /> 如果不存在，则默认类型是菜单。<br /><br /> 上下文<br /> 当用户右键单击一个窗口，显示快捷菜单。 快捷菜单还拥有以下特征：<br /><br /> -时不使用父和优先级字段菜单是显示为快捷菜单。<br />-可以使用子菜单，而且还显示为快捷菜单。 在这种情况下，遵循组 ID 和优先级字段。<br />-是不始终可用。<br /><br /> 仅当以下条件为真时，显示快捷菜单：<br /><br /> 的将显示承载它窗口。<br />的在 VSPackage 中鼠标处理程序检测到窗口上的右键单击，然后调用处理命令的方法。<br />-的快捷菜单显示通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A>方法 （建议） 或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>方法。<br /><br /> 菜单<br /> 提供一个下拉列表菜单。 下拉列表菜单还拥有以下特征：<br /><br /> -尊重其定义中的父级。<br />-必须具有父组或到组 CommandPlacement。<br />-可以是菜单的任何其他类型中的子菜单。<br />-将自动显示时显示其父菜单。<br />-不需要任何 VSPackage 代码，使它显示的实现。<br /><br /> MenuController<br /> 提供一个拆分按钮下拉列表菜单，其中通常使用工具栏中。 MenuController 菜单还拥有以下特征：<br /><br /> -必须包含在通过父或 CommandPlacement 的另一个菜单。<br />-尊重其定义中的父级。<br />-可有其父菜单的任何类型。<br />-自动成为可用时显示其父菜单。<br />-不需要编程支持，以使显示的菜单。<br /><br /> 拆分按钮菜单中的命令将显示在菜单按钮。 显示该命令具有以下特征之一：<br /><br /> -它是已使用，如果该命令仍显示和启用的最后一个命令。<br />-它是第一个显示的命令。<br /><br /> MenuControllerLatched<br /> 提供为其指定的命令可以为默认选择通过将命令标记为锁定了拆分按钮下拉列表菜单。<br /><br /> 锁定的命令是在中标记为已选中，菜单通常通过显示复选标记的命令。 命令将标记为锁定是否 OLECMDF_LATCHED 标志中的实现在其上设置`QueryStatus`方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。 MenuControllerLatched 菜单还拥有以下特征：<br /><br /> -必须包含在父组或 CommandPlacement 通过另一个菜单。<br />-尊重其定义中的父级。<br />-可有其父菜单的任何类型。<br />-是可显示其父菜单时的不同而不同。<br />-不需要编程支持，以使显示的菜单。<br /><br /> 拆分按钮菜单中的命令将显示在菜单按钮。 显示该命令具有以下特征之一：<br /><br /> -它是第一个显示的命令锁定。<br />-它是第一个显示的命令。<br /><br /> Toolbar<br /> 提供一个工具栏。 工具栏具有以下特征：<br /><br /> -将忽略其定义中的父级。<br />-无法将甚至不通过使用 CommandPlacement 进行任何组的子菜单。<br />-始终可以通过单击显示**工具栏**上**视图**菜单。<br />-可以通过使用显示[VisibilityItem](../extensibility/visibilityitem-element.md)。<br />-不需要任何代码来创建它。 有关如何创建工具栏的示例，请参阅[将工具栏添加](../extensibility/adding-a-toolbar.md)。<br /><br /> ToolWindowToolbar<br /> 提供一个工具栏，它附加到特定工具窗口，就像工具栏附加到开发环境。<br /><br /> -将忽略其定义中的父级。<br />-无法将甚至不通过使用 CommandPlacement 进行任何组的子菜单。<br />-仅当承载工具栏的工具窗口将显示并 VSPackage 显式将工具栏添加到工具窗口将显示。 这通常是通过获取工具栏主机属性创建工具窗口时 (由表示<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost>接口) 从工具窗口框架，然后调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A>方法。|  
|条件|可选。 请参阅[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|父级|可选。 菜单项的父元素。|  
|CommandFlag|必需。 请参阅[命令标志元素](../extensibility/command-flag-element.md)。 菜单 CommandFlag 有效值如下所示：<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -此标志不会影响显示的工具栏。<br />-   **DontCache**<br />-   **DynamicVisibility** -此标志不会影响显示的工具栏。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|字符串|必需。 请参阅[字符串元素](../extensibility/strings-element.md)。 子`ButtonText`必须定义元素。|  
|批注|可选注释。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Menus 元素](../extensibility/menus-element.md)|定义 VSPackage 实现的所有菜单。|  
  
## <a name="example"></a>示例  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)