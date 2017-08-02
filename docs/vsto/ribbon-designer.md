---
title: "功能区设计器"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "控件 [Visual Studio 中的 Office 开发], 功能区"
  - "自定义功能区"
  - "自定义功能区, 关于功能区设计器"
  - "自定义功能区"
  - "自定义功能区, 关于功能区设计器"
  - "设计器 [Visual Studio 中的 Office 开发], 功能区"
  - "只读属性"
  - "功能区 [Visual Studio 中的 Office 开发], 常规任务"
  - "功能区 [Visual Studio 中的 Office 开发], 控件"
  - "功能区 [Visual Studio 中的 Office 开发], 自定义"
  - "功能区 [Visual Studio 中的 Office 开发], 快捷键"
  - "功能区 [Visual Studio 中的 Office 开发], 可视设计器"
  - "功能区设计器 [Visual Studio 中的 Office 开发]"
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# 功能区设计器
  功能区设计器是一个可视化设计画布。  使用功能区设计器可以将自定义选项卡、组和控件添加到 Microsoft Office 应用程序的功能区。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 若要打开功能区设计器，请将**“功能区\(可视化设计器\)”**项添加到项目。  然后，可以使用设计工具完成以下任务：  
  
-   [设计功能区布局](#DesigningRibbonLayout)  
  
-   [处理事件和设置控件属性](#HandleEventsSetProperties)  
  
-   [添加控件到 Backstage 视图](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  有一些任务无法通过使用功能区设计器来完成。  有关这些任务以及如何才能完成它们的更多信息，请参见[功能区概述](../vsto/ribbon-overview.md)。  
  
 ![链接到视频](~/docs/data-tools/media/playvideo.gif "链接到视频") 有关相关视频演示，请参见 [How Do I: Use the Ribbon Designer to Customize the Ribbon in Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312)（如何实现：使用功能区设计器在 Outlook 中自定义功能区？）。  
  
## 将功能区（可视化设计器）项添加到项目  
 若要使用功能区设计器，请将一个新的**“功能区\(可视化设计器\)”**项添加到项目。  有关详细信息，请参阅 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
 在添加新的**“功能区\(可视化设计器\)”**项时，Visual Studio 会自动将以下文件添加到项目中：  
  
-   功能区代码文件。  此文件的名称是您在**“添加新项”**对话框中为**“功能区\(可视化设计器\)”**项指定的名称。  请向此文件添加用于处理功能区事件的代码。  
  
-   一个功能区设计器代码文件。  此文件包含由功能区设计器生成的代码，不应直接编辑此文件。  
  
-   一个资源文件。  此文件包含功能区上的每个控件的属性值。  
  
 如果您已拥有一个来自其他项目的**“功能区\(可视化设计器\)”**项，则可以通过**“添加现有项”**对话框在当前项目中重用该项。  
  
##  <a name="DesigningRibbonLayout"></a> 设计功能区  
 可通过三种方式打开功能区设计器：  
  
-   在**“解决方案资源管理器”**中双击功能区代码文件。  
  
-   在**“解决方案资源管理器”**中，右击功能区代码文件，然后单击**“视图设计器”**。  
  
-   在**“解决方案资源管理器”**中选择功能区代码文件，然后在**“视图”**菜单上，单击**“设计器”**。  
  
 功能区设计器包含一个默认选项卡和组。  可以从功能区设计器中移除该默认选项卡和组。  若要移除默认组，请右击**“Group1”**，然后单击**“删除”**。  若要移除默认选项卡，请右击设计图面的空白区域，然后单击**“‘删除功能区’选项卡”**。  
  
 还可以将自定义选项卡、组和控件添加到功能区设计器。  在**“Office 功能区控件”**组中的**“工具箱”**中可以找到这些控件。  可以通过三种方式将**“Office 功能区控件”**组中的控件添加到功能区设计器：  
  
-   将控件拖动到功能区设计器上的合适区域。  
  
-   单击一个控件，然后单击功能区设计器中的合适区域。  
  
-   在设计器中选择一个合适区域，然后在**“工具箱”**中双击一个控件。  
  
### 功能区设计工作流  
 请按照下列基本步骤来设计功能区布局：  
  
1.  [向功能区中添加自定义选项卡](#AddTabToRibbon)。  
  
2.  [将组添加到选项卡](#AddGroupsToTab)。  
  
3.  [将控件添加到组](#AddControlsToGroups)。  
  
 只能将控件放置在组上；不能直接将控件拖动到选项卡或功能区上。  只能将组放置在选项卡上；不能直接将组拖动到功能区上。  
  
 通过将控件拖动到正确位置来排列控件。  在**“属性”**窗口中，可以设置控件的属性。  
  
 不能在功能区上将控件从一个选项卡拖动到另一个选项卡。  如果要将一个控件移动到另一个选项卡，必须使用**“剪切”**命令从一个选项卡中移除该控件，然后将其粘贴到另一个选项卡上。  如果您确实剪切并粘贴了控件，则事件处理程序会停止工作。  可以在**“属性”**窗口中重新连接事件处理程序。  有关详细信息，请参阅 [“属性”窗口](../ide/reference/properties-window.md)。  
  
###  <a name="AddTabToRibbon"></a> 向功能区中添加自定义选项卡  
 可通过三种方式向功能区中添加自定义选项卡：  
  
-   从**“工具箱”**添加选项卡。  
  
-   右击功能区设计器，然后单击**“‘添加功能区’选项卡”**。  
  
-   打开**“Tab 集合编辑器”**，然后单击**“添加”**。  
  
     若要打开**“Tab 集合编辑器”**，请在**“属性”**窗口中选择**“Tab”**属性，然后单击省略号按钮 ![ASP.NET 移动设计器中的省略号](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")。  
  
 添加选项卡后，可以添加组以包含控件。  
  
#### 从功能区移除自定义选项卡  
 可通过三种方式从功能区移除自定义选项卡：  
  
-   右击设计器，然后单击**“‘删除功能区’选项卡”**。  
  
-   在**“属性”**窗口的**“命令”**窗格中，单击**“‘删除功能区’选项卡”**。  
  
-   打开**“Tab 集合编辑器”**，选择选项卡，然后单击**“移除”**。  
  
#### 更改功能区上选项卡的位置  
 可以更改功能区上自定义选项卡的顺序。  还可以将自定义选项卡放置在功能区上内置选项卡的前面和后面。  有关详细信息，请参阅 [如何：更改功能区上选项卡的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)。  
  
#### 自定义功能区上的内置选项卡  
 内置选项卡是 Microsoft Office 应用程序的功能区上已存在的选项卡。  例如，**“数据”**选项卡是 Excel 中的内置选项卡。  
  
 在内置选项卡中可以添加组和控件。  默认情况下，自定义组会显示为内置选项卡上的最后一个组，不过您可以将其移动至选项卡上的任何内置组之前或之后。  
  
 无法移除内置组。  
  
 有关如何自定义内置选项卡的详细信息，请参见[如何：自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)。  
  
###  <a name="AddGroupsToTab"></a> 将组添加到选项卡  
 组按照逻辑关系组织功能区上的控件。  将组添加到选项卡。  将所有其他控件添加到组。  
  
###  <a name="AddControlsToGroups"></a> 将控件添加到组  
 将一个或多个控件添加到组。  下表描述每个控件。  
  
|控件|描述|  
|--------|--------|  
|**方框**|一个对组中的控件进行组织的容器。  可以将除分隔线、组或选项卡之外的任何控件添加到框。  框可以是水平的，也可以是垂直的。|  
|**按钮**|一个启动操作的按钮。  可以将按钮添加到组、按钮组、下拉列表、库、菜单或拆分按钮。|  
|**ButtonGroup**|一个组，包含一个或多个按钮、切换按钮、菜单、拆分按钮和库。  可以将按钮组添加到组或菜单。|  
|**CheckBox**|一个框，可以选中或清除它以打开或关闭一个选项。|  
|**ComboBox**|一个具有附加列表框的编辑框。  用户可以键入或选择其选项。  该框显示当前选择。  使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> 属性可以在功能区加载到 Office 应用程序中之前或之后在运行时添加和移除项。|  
|**DropDown**|一个列表，包含用户可以选择的项。  用户无法在下拉列表中键入新项。<br /><br /> 使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> 属性可以向该列表添加项。  可以在运行时添加和移除项。<br /><br /> 使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> 属性可以向该列表添加按钮。  但是，在运行时，无法在功能区加载到 Office 应用程序中之后添加和移除按钮。|  
|**EditBox**|一个框，用户可以在其中键入文本。|  
|**Gallery**|一个菜单，提供用户可以从中进行选择的可视化选项的数组或网格。  可以控制该菜单中的选项的布局。  使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> 和 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 属性可以指定要显示库的项和按钮的行数和列数。|  
|**Label**|可以用于标识功能区上的控件的文本。|  
|**菜单**|一个下拉列表，可以包含以下任何控件：<br /><br /> -   按钮<br />-   Check box<br />-   Gallery<br />-   菜单<br />-   Split button<br />-   切换按钮<br />-   Separator<br /><br /> 若要在功能区设计器中向菜单添加控件，请单击菜单中的下箭头以显示菜单设计图面。  然后，可以将功能区控件从**“工具箱”**拖动至菜单上。  若要排列控件，请将控件拖动至所需位置。<br /><br /> 若要在功能区加载到 Office 应用程序中之后向 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> 添加控件，必须在功能区加载之前将 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> 属性设置为 **true**。  有关如何执行此操作的信息，请参见[功能区对象模型概述](../vsto/ribbon-object-model-overview.md)。|  
|**Separator**|一条用于分隔列表中的项的细线。  在添加到组时，该线条是垂直的。  在添加到菜单时，该线条是水平的。|  
|**SplitButton**|一个具有附加菜单的按钮。  拆分按钮可以包含以下任何控件：<br /><br /> -   按钮<br />-   Check box<br />-   Gallery<br />-   菜单<br />-   Split button<br />-   切换按钮<br />-   Separator<br /><br /> 与菜单类似，拆分按钮具有其自己的设计图面。  但是，与菜单不同的是，您只能在功能区加载到 Office 应用程序中之前更新拆分按钮中的项。  有关如何更新拆分按钮中的项的信息，请参见[功能区对象模型概述](../vsto/ribbon-object-model-overview.md)。|  
|**ToggleButton**|一个显示按下或未按下状态的按钮。|  
  
##  <a name="HandleEventsSetProperties"></a> 处理事件和设置属性  
 使用功能区设计器可以在设计时通过**“属性”**窗口设置控件属性。  此外，功能区公开了一个强类型对象模型，使用该模型可以在运行时获取和设置功能区控件的属性。  
  
 双击设计器上的任何控件均可打开针对该控件的默认事件的事件处理程序。  使用**“属性”**窗口可为所有其他控件事件创建事件处理程序。  
  
 功能区的事件和属性位于 <xref:Microsoft.Office.Tools.Ribbon> 命名空间中。  **“功能区\(可视化设计器\)”**项会自动在项目中添加对此程序集的引用，并在功能区代码文件的开头插入适当的 **using** 或 **Imports** 语句。  
  
 有关在运行时处理功能区事件和设置功能区控件的属性的信息，请参见[功能区对象模型概述](../vsto/ribbon-object-model-overview.md)。  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> 自定义 Backstage 视图  
 您可以使用功能区设计器向单击“文件”选项会打开的菜单中添加控件。  此菜单称为 Backstage 视图。  
  
 您无法使用功能区设计器在内置控件前后放置控件。  内置控件是已经出现在 Backstage 视图中的控件。  如果要将控件放在内置控件的前面或后面，则必须使用功能区 XML。  有关“功能区 \(XML\)”的详细信息，请参见 [功能区 XML](../vsto/ribbon-xml.md)。  有关自定义 Backstage 视图的更多信息，请参见 [Introduction to the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182189)（Office 2010 Backstage 视图简介 \- 适用于开发人员）和  [Customizing the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182188)（自定义 Office 2010 Backstage 视图 \- 适用于开发人员）。  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 有关如何向 Backstage 视图添加控件的信息，请参见 [如何：向 Backstage 视图添加控件](../vsto/how-to-add-controls-to-the-backstage-view.md)。  
  
##  <a name="Accessibility"></a> 功能区设计器中的辅助功能  
 使用键盘快捷键可以移动功能区设计器中的控件。  某些键盘快捷键适用于所有控件，而某些仅适用于具有菜单的控件。  
  
 下表显示了适用于所有控件的键盘快捷键。  
  
|操作|键盘快捷键|  
|--------|-----------|  
|将控件移动至列表中上一个控件之前。|Ctrl\+向上键<br /><br /> Ctrl\+向左键|  
|将控件移动至列表中下一个控件之后。|Ctrl\+向下键<br /><br /> Ctrl\+向右键|  
|将选定内容从一个控件移动至同一组中的另一个控件。  对于下拉面板，在父控件与下拉面板中的控件之间移动选定内容。|向上键<br /><br /> 向下键|  
|向前循环访问所有控件。|Tab|  
|向后循环访问所有控件。|Shift\+Tab|  
|删除选定的一个控件或一组控件。|Delete|  
|复制选定的控件。|Ctrl\+C|  
|剪切选定的控件。|Ctrl\+X|  
|从剪贴板中粘贴控件。|Ctrl\+V|  
|选择**“工具箱”**。|Ctrl\+Alt\+X|  
|选择父组件。|Esc|  
  
 下表中显示了仅适用于 Microsoft Office 菜单、<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> 和 <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 的键盘快捷键。  
  
|操作|键盘快捷键|  
|--------|-----------|  
|如果下拉面板已打开，并且在下拉面板上选择了一个控件，则选择父控件。|向左键|  
|如果下拉面板已打开，并且选择了父控件，则关闭下拉面板。|向左键|  
|打开下拉面板。|向右键|  
|如果下拉面板已打开，则选择下拉面板上的第一个控件。|向右键|  
|关闭下拉面板。|Esc|  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [如何：将功能区从功能区设计器导出为功能区 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  