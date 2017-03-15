---
title: "Menu 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 架构元素菜单"
  - "菜单元素 (VSCT XML 架构)"
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Menu 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义一个菜单项。 下面列出了菜单六种: 上下文、 菜单、 MenuController、 MenuControllerLatched、 工具栏和 ToolWindowToolbar。  
  
## 语法  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|guid|必需。 ID 的 GUID 的命令标识符的 GUID。|  
|id|必需。 ID 的 GUID 的命令标识符的 ID。|  
|priority|可选。 指定的相对位置的一个菜单的菜单组中一个数值。|  
|ToolbarPriorityInBand|可选。 一个数值，窗口停靠时在带区指定工具栏的相对位置。|  
|类型|可选。 一个枚举的值，指定的元素的种类。<br /><br /> 如果不存在，则默认类型是菜单。<br /><br /> 上下文<br /> 当用户右击一个窗口，显示快捷菜单。 快捷菜单还拥有以下特征:<br /><br /> -   作为快捷菜单，显示菜单时，不使用父和优先级字段。<br />-   可以使用为子菜单，而且还作为一个快捷菜单。 在这种情况下，会考虑组 ID 和优先级字段。<br />-   并非始终可用。<br /><br /> 仅在下列条件为真时，将显示一个快捷菜单:<br /><br /> -   显示的窗口中承载它。<br />-   鼠标处理程序在 VSPackage 中的检测到窗口中右键单击，然后调用的方法用于处理该命令。<br />-   通过调用显示快捷菜单 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 方法 \(建议\) 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 方法。<br /><br /> 菜单<br /> 提供一个下拉列表菜单。 下拉列表菜单还拥有以下特征:<br /><br /> -   会保留其定义中的父级。<br />-   必须具有父组或向组 CommandPlacement。<br />-   可以是菜单的任何其他类型中的子菜单。<br />-   将自动显示时显示其父菜单。<br />-   不需要任何 VSPackage 代码，使其显示的实现。<br /><br /> MenuController<br /> 提供了一个拆分按钮的下拉列表菜单，其中通常在工具栏中使用。 MenuController 菜单还拥有以下特征:<br /><br /> -   必须包含在父域或 CommandPlacement 通过另一个菜单。<br />-   会保留其定义中的父级。<br />-   可以有任何种类的菜单中作为其父级。<br />-   会自动成为可用时显示其父菜单。<br />-   不需要编程支持，以使显示的菜单。<br /><br /> 拆分按钮菜单中的命令将显示在菜单按钮。 该命令显示具有以下特征之一:<br /><br /> -   它是如果仍显示和启用该命令使用的最后一个命令。<br />-   它是第一个显示的命令。<br /><br /> MenuControllerLatched<br /> 提供为其命令可以指定为默认选择通过将该命令标记为已锁定拆分按钮下拉菜单。<br /><br /> 锁定的命令是在中标记为已选中，菜单通常通过显示复选标记的命令。 可以标记一个命令，为闩锁是否 OLECMDF\_LATCHED 标志的实现中在其上设置 `QueryStatus` 方法 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口。 MenuControllerLatched 菜单还拥有以下特征:<br /><br /> -   必须包含在父组或 CommandPlacement 通过另一个菜单。<br />-   会保留其定义中的父级。<br />-   可以有任何种类的菜单中作为其父级。<br />-   将可用时显示其父菜单。<br />-   不需要编程支持，以使显示的菜单。<br /><br /> 拆分按钮菜单中的命令将显示在菜单按钮。 该命令显示具有以下特征之一:<br /><br /> -   它是闩锁的第一个显示的命令。<br />-   它是第一个显示的命令。<br /><br /> Toolbar<br /> 提供的工具栏。 工具栏具有以下特征:<br /><br /> -   将忽略其定义中的父级。<br />-   无法进行的任何组的子菜单甚至不通过使用 CommandPlacement。<br />-   始终可以通过单击显示 **工具栏** 上 **视图** 菜单。<br />-   可以通过使用显示 [VisibilityItem](0932f551-972d-4194-84bb-426e3e4375e4Vis)。<br />-   不需要任何代码来创建它。 有关如何创建工具栏的示例，请参阅 [将工具栏添加](../extensibility/adding-a-toolbar.md)。<br /><br /> ToolWindowToolbar<br /> 就像一个工具栏附加到开发环境，提供了附加到特定的工具窗口，一个工具栏。<br /><br /> -   将忽略其定义中的父级。<br />-   无法进行的任何组的子菜单甚至不通过使用 CommandPlacement。<br />-   只有当显示的工具窗口承载工具栏上，并且 VSPackage 显式将工具栏添加到工具窗口中显示。 这通常是通过获取的工具栏上的主机属性创建工具窗口 \(由表示 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> 接口\) 从工具窗口框架，然后调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> 方法。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|父级|可选。 菜单项的父元素。|  
|CommandFlag|必需。 请参阅 [命令标志元素](../extensibility/command-flag-element.md)。 一个菜单 CommandFlag 有效值如下所示:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** \-此标志不会影响显示工具栏。<br />-   **DontCache**<br />-   **DynamicVisibility** \-此标志不会影响显示工具栏。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|字符串|必需。 请参阅 [字符串元素](../extensibility/strings-element.md)。 子 `ButtonText` 必须定义元素。|  
|批注|可选注释。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[菜单元素](../extensibility/menus-element.md)|定义 VSPackage 实现的所有菜单。|  
  
## 示例  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget" priority="0x0002" type="Menu"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>Edit Widget</ButtonText> </Strings> </Parent> </Menu>  
```  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)