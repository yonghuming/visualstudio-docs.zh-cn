---
title: "功能区对象模型概述 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Ribbon [Office development in Visual Studio], object model
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: "75"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 655a1b6f3d57ac15fc7a50a603b2a12791251c9d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ribbon-object-model-overview"></a>功能区对象模型概述
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]公开一个可用于获取和设置在运行时的功能区控件的属性的强类型的对象模型。 例如，你可以动态填充菜单控件，或显示和隐藏控件根据上下文。 向功能区，但只能在功能区加载 Office 应用程序之前，还可以添加选项卡、 组和控件。 有关信息，请参阅[设置变成只读属性的属性](#SettingReadOnlyProperties)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 此功能区对象模型包含的主要[功能区类](#RibbonClass)，[功能区事件](#RibbonEvents)，和[功能区控件类](#RibbonControlClasses)。  
  
##  <a name="RibbonClass"></a>功能区类  
 添加新**功能区 （可视化设计器）** Visual Studio 将添加到项目，项**功能区**到你的项目的类。 **功能区**类继承自<xref:Microsoft.Office.Tools.Ribbon.RibbonBase>类。  
  
 此类显示为功能区代码文件和功能区设计器代码文件之间拆分的分部类。  
  
##  <a name="RibbonEvents"></a>功能区事件  
 **功能区**类包含以下三个事件：  
  
|Event|描述|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Office 应用程序加载功能区自定义项时引发。 <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>事件处理程序将自动添加到功能区代码文件。 使用此事件处理程序功能区加载时运行自定义代码。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|可以为功能区自定义项中的缓存图像何时在功能区加载。 如果你编写代码以缓存此事件处理程序中的功能区映像，你可以获取的略微的性能有所提高。 有关更多信息，请参见<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|功能区实例关闭时引发。|  
  
##  <a name="RibbonControlClasses"></a>功能区控件  
 <xref:Microsoft.Office.Tools.Ribbon>命名空间包含在中看到每个控件的类型**Office 功能区控件**组**工具箱**。  
  
 下表显示每个类型`Ribbon`控件。 有关每个控件的说明，请参阅[功能区概述](../vsto/ribbon-overview.md)。  
  
|控件名称|类名|  
|------------------|----------------|  
|**框**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**组合框**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**下拉列表中**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**编辑框**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**库**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**组**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**标签**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**菜单**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**分隔符**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**拆分按钮**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**选项卡**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**切换按钮**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon>命名空间使用这些类型的"功能区"前缀以避免名称冲突，名称中的控件类<xref:System.Windows.Forms>命名空间。  
  
 当将控件添加到功能区设计器时，功能区设计器会将该控件类声明为功能区设计器代码文件中的字段。  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>使用功能区控件的属性的常见任务  
 每个`Ribbon`控件包含可用于执行各种任务，如将标签分配到控件，或隐藏和显示控件的属性。  
  
 在某些情况下，属性将变为只读在功能区加载之后，或者在将控件添加到动态菜单。 有关详细信息，请参阅[设置属性该变成只读](#SettingReadOnlyProperties)。  
  
 下表介绍了一些你可以使用执行的任务`Ribbon`控件属性。  
  
|对于此任务：|执行此操作：|  
|--------------------|--------------|  
|隐藏或显示一个控件。|使用可见的属性。|  
|启用或禁用控件。|使用的 Enabled 属性。|  
|设置控件的大小。|使用 ControlSize 属性。|  
|获取在控件显示的图像。|使用映像属性。|  
|更改控件的标签。|使用标签属性。|  
|向控件添加用户定义的数据。|使用标记属性。|  
|获取项<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>， <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>， <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>，或<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>控件。|使用项目属性。|  
|将项添加到<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>， <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>，或<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>控件。|使用项目属性。|  
|将控件添加到<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>。|使用项目属性。<br /><br /> 若要将控件添加到<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>功能区加载到 Office 应用程序后，你必须设置<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>属性**true**功能区加载到 Office 应用程序之前。 有关信息，请参阅[设置变成只读属性的属性](#SettingReadOnlyProperties)。|  
|获取的选定的项<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>，<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|使用 SelectedItem 属性。 有关<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>，使用<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>属性。|  
|获取组上<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>。|使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> 属性。|  
|指定行和列中显示的数<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>。|使用<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>和<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>属性。|  
  
##  <a name="SettingReadOnlyProperties"></a>变为只读设置属性  
 某些属性仅在功能区加载之前设置。 有以下三个位置设置这些属性：  
  
-   在 Visual Studio**属性**窗口。  
  
-   构造函数中**功能区**类。  
  
-   中的 CreateRibbonExtensibilityObject 方法`ThisAddin`， `ThisWorkbook`，或`ThisDocument`的你的项目的类。  
  
 动态菜单提供一些例外情况。 你可以创建新的控件、 设置其属性，然后将它们添加到动态菜单在运行时，即使加载的功能区上包含的菜单。  
  
 你将添加到动态菜单的控件的属性可以在任何时间设置。  
  
 有关详细信息，请参阅[属性该变成只读](#ReadOnlyProperties)。  
  
### <a name="setting-properties-in-the-constructor-of-the-ribbon"></a>在功能区的构造函数中设置属性  
 你可以设置的属性`Ribbon`的构造函数中的控件**功能区**类。 此代码必须出现在调用之后`InitializeComponent`方法。 下面的示例： 将新按钮添加到组，如果当前时间为 17:00 太平洋时间 (UTC-8) 或更高版本。  
  
 添加以下代码。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 在 Visual C# 项目中从 Visual Studio 2008 升级，该构造函数出现在功能区代码文件中。  
  
 在 Visual Basic 项目中，或在 Visual C# 项目中创建[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]，构造函数将显示在功能区设计器代码文件中。 此文件命名为*YourRibbonItem*。Designer.cs 或*YourRibbonItem*。Designer.vb。 若要查看此文件在 Visual Basic 项目，必须首先单击**显示所有文件**在解决方案资源管理器的按钮。  
  
### <a name="setting-properties-in-the-createribbonextensibilityobject-method"></a>在 CreateRibbonExtensibilityObject 方法中设置属性  
 你可以设置的属性`Ribbon`控制当你重中`ThisAddin`， `ThisWorkbook`，或`ThisDocument`的你的项目的类。 有关 CreateRibbonExtensibilityObject 方法的详细信息，请参阅[功能区概述](../vsto/ribbon-overview.md)。  
  
 下面的示例的 CreateRibbonExtensibilityObject 方法中设置功能区属性`ThisWorkbook`的 Excel 工作簿项目的类。  
  
 添加以下代码。  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a>变成只读属性的属性  
 下表显示只能在功能区加载之前设置的属性。  
  
> [!NOTE]  
>  你可以随时设置动态菜单上的控件的属性。 此表不适用于这种情况下。  
  
|属性|功能区控件类|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**列数**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**动态**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**组**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**位置**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**行计数**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**选项卡**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**标题**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="setting-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>在 Outlook 检查器中显示功能区的设置属性  
 每当用户打开检查器功能区将显示，都会创建功能区的新实例。 但是，你可以设置仅在创建功能区的第一个实例之前，在上表中列出的属性。 第一个实例创建之后，是因为第一个实例定义了 Outlook 用于加载功能区 XML 文件变为只读这些属性。  
  
 如果你有任何这些属性设置为不同的值创建功能区的其他实例时的条件逻辑，此代码将不起。  
  
> [!NOTE]  
>  确保**名称**属性设置为每个控件添加到 Outlook 功能区。 如果在运行时将控件添加到 Outlook 功能区中，你必须在代码中设置此属性。 如果在设计时将控件添加到 Outlook 功能区中，将自动设置 Name 属性。  
  
## <a name="ribbon-control-events"></a>功能区控件事件  
 每个控件类包含一个或多个事件。 下表描述这些事件。  
  
|Event|描述|  
|-----------|-----------------|  
|单击|单击控件时发生。|  
|宽度|编辑框或组合框的文本更改时发生。|  
|ItemsLoading|控件的项集合请求按办公室时发生。 Office 缓存项集合，直到你的代码更改的控件的属性或调用<xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A>方法。|  
|按钮单击|中的按钮时发生<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>或<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>单击。|  
|SelectionChanged|发生时中的选定<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>或<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>更改。|  
|DialogLauncherClick|单击一个组的右下角中的对话框启动器图标时发生。|  
  
 这些事件的事件处理程序具有以下两个参数。  
  
|参数|描述|  
|---------------|-----------------|  
|*发件人*|<xref:System.Object>它表示引发事件的控件。|  
|*e*|A<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>包含<xref:Microsoft.Office.Core.IRibbonControl>。 使用此控件访问在提供的功能区对象模型中不可用的任何属性[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。|  
  
## <a name="see-also"></a>另请参阅  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能区概述](../vsto/ribbon-overview.md)   
 [如何： 开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [演练： 使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练： 在运行时更新功能区上的控件](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何： 自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何： 将控件添加到 Backstage 视图](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何： 将功能区从功能区设计器导出到功能区 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：显示外接程序用户界面错误](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  