---
title: "功能区设计器 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: "79"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 941ca002d2f840805253624e7e0004fb560c4167
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ribbon-designer"></a>功能区设计器
  功能区设计器是一个可视化设计画布。 功能区设计器用于将自定义选项卡、 组和控件添加到 Microsoft Office 应用程序的功能区。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 若要打开功能区设计器，请添加**功能区 （可视化设计器）**到你的项目的项。 然后，就可以使用的设计工具的以下任务：  
  
-   [设计功能区布局](#DesigningRibbonLayout)  
  
-   [处理事件，并设置控件属性](#HandleEventsSetProperties)  
  
-   [将控件添加到 Backstage 视图](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  将使用功能区设计器无法完成某些任务。 有关这些任务和如何完成它们的详细信息，请参阅[功能区概述](../vsto/ribbon-overview.md)。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何： 使用功能区设计器自定义 Outlook 中的功能区？](http://go.microsoft.com/fwlink/?LinkID=130312)。  
  
## <a name="adding-a-ribbon-visual-designer-item-to-a-project"></a>向项目中添加功能区 （可视化设计器） 项  
 若要使用功能区设计器，添加新**功能区 （可视化设计器）**到你的项目的项。 有关详细信息，请参阅 [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
 添加新**功能区 （可视化设计器）**项，Visual Studio 会自动添加以下文件到你的项目：  
  
-   功能区代码文件。 此文件具有你为指定的名称**功能区 （可视化设计器）**中项**添加新项**对话框。 添加代码来处理对此文件的功能区事件。  
  
-   功能区设计器代码文件。 此文件包含功能区设计器所生成的代码，不应直接编辑。  
  
-   资源文件。 此文件包含功能区上的每个控件的属性值。  
  
 如果你已有**功能区 （可视化设计器）**项从另一个项目，您可以通过重新使用它当前项目中使用**添加现有项**对话框。  
  
##  <a name="DesigningRibbonLayout"></a>设计功能区  
 有三种方法打开功能区设计器：  
  
-   在**解决方案资源管理器**，双击功能区代码文件。  
  
-   在**解决方案资源管理器**，功能区代码文件中，右键单击，然后单击**视图设计器**。  
  
-   在**解决方案资源管理器**，选择功能区代码文件中，，然后单击**设计器**上**视图**菜单。  
  
 功能区设计器包含一个默认选项卡和组。 可以从功能区设计器中删除的默认选项卡和组。 若要删除默认组，右键单击**Group1**，然后单击**删除**。 要删除默认选项卡，右键单击设计图面的空白区域，然后单击**删除功能区选项卡**。  
  
 你可以将自定义选项卡、 组和控件添加到功能区设计器中。 你可以找到这些控件在**工具箱**中**Office 功能区控件**组。 有三种方法来添加控件从**Office 功能区控件**组到功能区设计器：  
  
-   功能区设计器上将控件拖到适当的区域中。  
  
-   单击控件，然后单击功能区设计器中的合适区域。  
  
-   在设计器中，选择相应的区域，然后双击中的控件**工具箱**。  
  
### <a name="ribbon-design-workflow"></a>功能区设计工作流  
 按照设计的功能区布局这些基本步骤：  
  
1.  [向功能区添加自定义选项卡](#AddTabToRibbon)。  
  
2.  [将组添加到选项卡](#AddGroupsToTab)。  
  
3.  [将控件添加到组](#AddControlsToGroups)。  
  
 控件仅可以删除组;无法将控件拖到选项卡直接或功能区。 可以仅在选项卡; 上删除组无法将组拖直接到功能区。  
  
 排列控件拖动到正确的位置。 你可以通过设置控件的属性**属性**窗口。  
  
 你无法将拖动控件从一个选项卡到另一个功能区。 如果你想要将控件移到另一个选项卡，则必须使用**剪切**命令删除控件从一个选项卡，然后再粘贴另一个选项卡上的控件。如果执行剪切的控件，并将其粘贴，事件处理程序将停止工作。 你可以重新连接中的事件处理程序**属性**窗口。 有关详细信息，请参阅[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
###  <a name="AddTabToRibbon"></a>向功能区添加自定义选项卡  
 有三种方法可以向功能区添加自定义选项卡：  
  
-   添加从选项卡**工具箱**。  
  
-   右键单击功能区设计器中，并依次**添加功能区选项卡**。  
  
-   打开**选项卡集合编辑器**，然后单击**添加**。  
  
     若要打开**选项卡集合编辑器**中**属性**窗口中，选择**选项卡**属性，然后单击省略号按钮![ASP.NET 移动设计器的椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆")。  
  
 添加选项卡后，你可以添加组以包含控件。  
  
#### <a name="removing-custom-tabs-from-the-ribbon"></a>从功能区中删除自定义选项卡  
 有三种方法可以从功能区中删除自定义选项卡：  
  
-   右键单击设计器中，并依次**删除功能区选项卡**。  
  
-   在**命令**窗格**属性**窗口中，单击**删除功能区选项卡**。  
  
-   打开**选项卡集合编辑器**，选择选项卡，然后单击**删除**。  
  
#### <a name="changing-the-position-of-a-tab-on-the-ribbon"></a>更改功能区上的选项卡的位置  
 你可以更改功能区上的自定义选项卡的顺序。 之前或之后在功能区上的内置选项卡，您还可以将自定义选项卡。 有关详细信息，请参阅[如何： 更改的功能区上的选项卡位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)。  
  
#### <a name="customizing-built-in-tabs-on-the-ribbon"></a>功能区上的自定义内置选项卡  
 内置选项卡是已在 Microsoft Office 应用程序的功能区的选项卡。 例如，**数据**选项卡是 Excel 中的内置选项卡。  
  
 可以将组和控件添加到内置选项卡。默认情况下，自定义组的显示作为最后一组内置选项卡上，但你可以将其移任何内置组之前或之后的选项卡上。  
  
 不能删除内置组。  
  
 有关如何自定义内置选项卡的详细信息，请参阅[如何： 自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)。  
  
###  <a name="AddGroupsToTab"></a>将组添加到选项卡  
 组按逻辑组织功能区上的控件。 将组添加到选项卡。 将所有其他控件添加到组。  
  
###  <a name="AddControlsToGroups"></a>将控件添加到组  
 将一个或多个控件添加到组。 下表介绍每个控件。  
  
|控件|描述|  
|-------------|-----------------|  
|**框**|将组织组中的控件的容器。 你可以除分隔符、 一个组或选项卡中添加任何控件。一个框可以水平或垂直。|  
|**Button**|一个启动操作的按钮。 可以将按钮添加到组、 按钮组、 下拉列表、 库、 菜单上，或拆分按钮。|  
|**ButtonGroup**|包含一个或多个按钮，切换按钮、 菜单、 拆分按钮和库的组。 可以将按钮组添加到组或菜单。|  
|**CheckBox**|一个框，可以选中或清除要打开或关闭一个选项。|  
|**组合框**|附加的列表框编辑框。 用户可以键入或者选择其选项。 框中显示当前所选内容。 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A>属性来添加和删除项目在运行时之前或之后功能区加载到 Office 应用程序。|  
|**下拉列表中**|用户可以选择的项的列表。 用户不能在下拉列表中键入新项。<br /><br /> 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A>属性将项添加到列表。 你可以添加和删除项目在运行时。<br /><br /> 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A>属性将按钮添加到列表。 但是，不能添加，并且在运行时功能区加载到 Office 应用程序之后删除按钮。|  
|**编辑框**|用户可以在其中键入文本的框。|  
|**库**|一个菜单，提供对数组或网格的可视化，用户可以从中选择的选项。 你可以控制在菜单中选择内容的布局。 使用<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>和<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>属性以指定的行和列将显示的项目数和库的按钮。|  
|**标签**|可用于标识功能区上的控件的文本。|  
|**菜单**|可以包含任何以下控件的下拉列表：<br /><br /> 按钮<br />-复选框<br />-库<br />菜单<br />拆分按钮<br />-切换按钮<br />-分隔符<br /><br /> 若要将控件添加到功能区设计器中的菜单中，单击菜单公开菜单设计图面中的向下箭头。 然后，可以将功能区控件从**工具箱**拖至菜单。 排列控件，请将它们拖到所需的位置。<br /><br /> 若要将控件添加到<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>功能区加载到 Office 应用程序后，你必须设置<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>属性**true**区加载之前。 有关如何执行此操作的信息，请参阅[功能区对象模型概述](../vsto/ribbon-object-model-overview.md)。|  
|**分隔符**|一个精简栏用于分隔列表中的项。 添加到组时，该线条是垂直的。 添加到菜单时，该线条是水平。|  
|**拆分按钮**|一个具有附加菜单按钮。 拆分按钮可以包含任何以下控件：<br /><br /> 按钮<br />-复选框<br />-库<br />菜单<br />拆分按钮<br />-切换按钮<br />-分隔符<br /><br /> 菜单上，与拆分按钮有其自己的设计图面。 但是，与菜单上，你只能在功能区加载到 Office 应用程序之前更新拆分按钮中的项。 有关如何更新拆分按钮中的项的信息，请参阅[功能区对象模型概述](../vsto/ribbon-object-model-overview.md)。|  
|**切换按钮**|将出现一个按钮的按下的或未按下状态。|  
  
##  <a name="HandleEventsSetProperties"></a>处理事件，并设置属性  
 功能区设计器使您能够通过使用在设计时设置控件属性**属性**窗口。 此外，功能区公开一个可用于获取和设置在运行时的功能区控件的属性的强类型的对象模型。  
  
 你可以双击要打开的事件处理程序控件的默认事件的设计器上的任何控件。 你可以通过创建的所有其他控件事件的事件处理程序**属性**窗口。  
  
 功能区事件和属性都位于<xref:Microsoft.Office.Tools.Ribbon>命名空间。 **功能区 （可视化设计器）**项会自动在项目中添加此程序集的引用，并插入适当**使用**或**导入**语句的顶部功能区代码文件。  
  
 有关处理功能区事件并在运行时设置的功能区控件的属性的信息，请参阅[功能区对象模型概述](../vsto/ribbon-object-model-overview.md)。  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a>自定义 Backstage 视图  
 你可以使用功能区设计器将控件添加到当单击打开菜单**文件**选项卡。此菜单称为 Backstage 视图。  
  
 您无法使用功能区设计器之前, 或之后内置控件定位控件。 内置控件是一个已出现在 Backstage 视图的控件。 如果你想要放置控件之前或之后内置控件，你必须使用功能区 XML。 有关详细信息**功能区 (XML)**，请参阅[功能区 XML](../vsto/ribbon-xml.md)。 有关自定义 Backstage 视图的详细信息，请参阅[开发人员在 Office 2010 Backstage 视图简介](http://go.microsoft.com/fwlink/?LinkId=182189)和[自定义开发人员在 Office 2010 Backstage 视图](http://go.microsoft.com/fwlink/?LinkId=182188)。  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 有关如何将控件添加到 Backstage 视图的信息，请参阅[如何： 将控件添加到 Backstage 视图](../vsto/how-to-add-controls-to-the-backstage-view.md)。  
  
##  <a name="Accessibility"></a>功能区设计器中的辅助功能  
 可以使用键盘快捷方式可在功能区设计器中移动控件。 某些键盘快捷方式适用于所有控件，并且某些仅适用于具有菜单的控件。  
  
 适用于所有控件的键盘快捷方式下表所示。  
  
|操作|键盘快捷键|  
|------------|-----------------------|  
|在列表中移动之前的上一个控件的控件。|CTRL + 向上<br /><br /> CTRL + 向左键|  
|完成列表中的下一个控件后移动控件。|CTRL + 向下<br /><br /> CTRL + 向|  
|将所选内容从一个控件移到同一组中的另一个。 为下拉列表面板中，父控件和下拉列表面板中的控件之间进行移动。|向上<br /><br /> 向下|  
|向前循环访问所有控件。|Tab|  
|通过所有控件向后循环。|Shift+Tab|  
|删除选定的控件或组控件。|DELETE|  
|将复制所选的控件。|Ctrl+C|  
|剪切所选的控件。|Ctrl+X|  
|粘贴剪贴板中的控件。|Ctrl+V|  
|选择**工具箱**。|Ctrl+Alt+X|  
|选择的父组件。|Esc|  
  
 仅适用于 Microsoft Office 菜单上，键盘快捷方式<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>，和<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>以下表所示。  
  
|操作|键盘快捷键|  
|------------|-----------------------|  
|如果下拉列表面板已打开并且没有在下拉列表面板上选择一个控件，请选择的父控件。|LEFT|  
|如果下拉列表面板已打开并且选择了父控件，请关闭下拉列表面板。|LEFT|  
|打开的下拉菜单的面板。|RIGHT|  
|如果下拉列表面板中处于打开状态，请选择下拉列表面板上的第一个控件。|RIGHT|  
|关闭下拉面板。|ESC|  
  
## <a name="see-also"></a>另请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练： 使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [如何： 将功能区从功能区设计器导出到功能区 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何： 开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  