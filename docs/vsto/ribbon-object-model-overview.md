---
title: "功能区对象模型概述 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "功能区 [Visual Studio 中的 Office 开发], 对象模型"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# 功能区对象模型概述
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 显示可用于获取和设置功能区控件属性在运行时的一个强类型对象模型。  例如，可以动态填充菜单控件，或者按照上下文显示和隐藏控件。  还可以添加选项卡、组和控件添加到功能区，但是，在功能区之前的 Office 应用程序只加载。  有关信息，请参见[设置变成只读属性的属性](#SettingReadOnlyProperties)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 此功能区对象模型主要由[功能区类](#RibbonClass)、[功能区事件](#RibbonEvents)和[功能区控件类](#RibbonControlClasses)组成。  
  
##  <a name="RibbonClass"></a> 功能区类  
 在添加新的 **功能区 \(可视化设计器\)** 项目项时，Visual Studio 会将 **Ribbon** 选件类添加到项目中。  **Ribbon** 类继承自 <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> 类。  
  
 此类作为在功能区代码文件和功能区设计器代码文件之间拆分的分部类出现。  
  
##  <a name="RibbonEvents"></a> 功能区事件  
 **Ribbon** 选件类包含以下三个操作：  
  
|Event|描述|  
|-----------|--------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|引发，在 Office 应用程序加载功能区自定义项。  <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> 事件处理程序会自动添加到功能区代码文件。  并在功能区加载时，使用此事件处理程序运行自定义代码。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|并在功能区加载时，允许您对功能区自定义项中缓存图像。  可以使性能稍有，如果您编写代码来缓存此事件处理程序的功能区图像。  有关详细信息，请参阅 <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|引发，后者在功能区实例关闭。|  
  
##  <a name="RibbonControlClasses"></a> 功能区控件  
 对于**“工具箱”**的**“Office 功能区控件”**组中显示的每个控件，<xref:Microsoft.Office.Tools.Ribbon> 命名空间都包含一个对应的类型。  
  
 下表显示了每个 `Ribbon` 控件的类型。  有关每个控件的说明，请参见[功能区概述](../vsto/ribbon-overview.md)。  
  
|控件名称|类名|  
|----------|--------|  
|**方框**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**按钮**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**组合**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**菜单**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon> 命名空间对这些类型使用“Ribbon”前缀，以避免与 <xref:System.Windows.Forms> 命名空间中的控件类的名称发生名称冲突。  
  
 向功能区设计器中添加控件时，功能区设计器会将该控件的类声明为功能区设计器代码文件中的一个字段。  
  
### 使用功能区控件属性的常规任务  
 每个 `Ribbon` 控件包含可以用来执行各种任务，如为控件指定标签或隐藏和显示控件的属性。  
  
 有时，在中，在功能区加载之后或控件添加到动态菜单后，属性将变为只读。  有关更多信息，请参见[设置变成只读属性的属性](#SettingReadOnlyProperties)。  
  
 下表描述了可以使用 `Ribbon` 控件属性，可以执行的一些任务。  
  
|对于此任务：|执行此操作：|  
|------------|------------|  
|隐藏或显示控件。|使用 Visible 属性。|  
|启用或禁用控件。|使用 Enabled 属性。|  
|设置控件的大小。|使用 ControlSize 属性。|  
|获取控件上显示的图像。|使用 Image 属性。|  
|更改控件的标签。|使用 Label 属性。|  
|向控件中添加用户定义的数据。|使用 Tag 属性。|  
|获取下列控件中的项：<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>、<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>、<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 或<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 控件。|使用 Items 属性。|  
|向 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>、<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 控件中添加项。|使用 Items 属性。|  
|向 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> 中添加控件。|使用 Items 属性。<br /><br /> 若要将控件添加到 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>，在功能区加载到 Office 应用程序之后，必须设置 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> 属性设置为 **true**，在功能区加载到 Office 应用程序。  有关信息，请参见[设置变成只读属性的属性](#SettingReadOnlyProperties)。|  
|获取下列控件的选定项：<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>、<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>。|使用 SelectedItem 属性。  对于 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>，使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> 属性。|  
|获取 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> 上的组。|使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> 属性。|  
|指定在 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 中显示的行数和列数。|使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 和 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> 属性。|  
  
##  <a name="SettingReadOnlyProperties"></a> 设置变成只读属性的属性  
 有些属性只能在功能区加载之前进行设置。  有三个位置可以设置这些属性：  
  
-   在 Visual Studio**“属性”**窗口中。  
  
-   在 **Ribbon** 选件类的构造函数。  
  
-   在项目的 `ThisAddin`、`ThisWorkbook` 或 `ThisDocument` 类的 CreateRibbonExtensibilityObject 方法中。  
  
 但对于动态菜单，情况则有不同。  您可以创建新控件，设置其属性，然后将它们添加到动态菜单运行时，在包含该菜单后的功能区加载。  
  
 可以随时设置添加到动态菜单的控件的属性。  
  
 有关更多信息，请参见[变成只读属性的属性](#ReadOnlyProperties)。  
  
### 在功能区的构造函数中设置属性  
 可以设置一个 `Ribbon` 控件的属性。**Ribbon** 选件类的构造函数。  该代码必须放在对 `InitializeComponent` 方法的调用之后。  下面的示例在当前时间为太平洋时间 \(UTC\-8\) 17:00 或更晚时向组中添加一个新按钮。  
  
 添加下列代码。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 在 Visual C\# 项目 \(从 Visual Studio 2008 升级，构造函数显示在功能区代码文件。  
  
 在 Visual Basic 项目中，或在 Visual C\# 项目在 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]创建的，构造函数显示在功能区设计器代码文件。  此文件名为 *YourRibbonItem*。Designer.cs 或 *YourRibbonItem*。. Designer.vb  若要查看 Visual Basic 项目中的此文件，必须先在解决方案资源管理器中单击**“显示所有文件”**按钮。  
  
### 在 CreateRibbonExtensibilityObject 方法中设置属性  
 当您重写在 `ThisAddin`、`ThisWorkbook`或项目中时，`ThisDocument` 选件类的 CreateRibbonExtensibilityObject 方法可以设置 `Ribbon` 控件的属性。  有关 CreateRibbonExtensibilityObject 方法的更多信息，请参见 [功能区概述](../vsto/ribbon-overview.md)。  
  
 下面的示例将在 Excel 工作簿项目的 `ThisWorkbook` 选件类的 CreateRibbonExtensibilityObject 方法的功能区属性。  
  
 添加下列代码。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> 变成只读属性的属性  
 下表显示了只能在功能区加载之前设置的属性。  
  
> [!NOTE]  
>  可以随时设置动态菜单上控件的属性。  该表不适用于这种情况。  
  
|Property|功能区控件类|  
|--------------|------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamic**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Groups**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**名称**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**制表符**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**标题**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### 设置 Outlook 检查器中显示的功能区的属性  
 功能区的新实例后，每当用户打开功能区上的检查器。  但是，因此，只有在功能区的第一个实例之前，可以设置上表中列出的属性。  在创建第一个实例之后，这些属性成为只读的，因为第一个实例定义 Outlook 用来加载功能区上的 XML 文件。  
  
 如果您具有设置这些属性中的任何一个为不同的值的条件逻辑，在功能区的其他实例后，此代码将不起作用。  
  
> [!NOTE]  
>  确保 **名称** 特性已添加到 Outlook 功能区中的每个控件设置。  如果将控件添加到 Outlook 功能区运行时，您必须在代码中设置此属性。  如果将控件添加到 Outlook 功能区在设计时，Name 自动设置属性。  
  
## 功能区控件事件  
 每个控件类都包含一个或多个事件。  下表描述了这些事件。  
  
|Event|描述|  
|-----------|--------|  
|Click|在单击控件时发生。|  
|TextChanged|在编辑框或组合框中的文本更改时发生。|  
|ItemsLoading|在 Office 请求控件的 Items 集合时发生。  Office 会缓存 Items 集合，直到代码更改控件的属性，或者调用 <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> 方法。|  
|ButtonClick|在单击 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 中的按钮时发生。|  
|SelectionChanged|在 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 中的所选内容更改时发生。|  
|DialogLauncherClick|在单击组右下角的对话框启动器图标时发生。|  
  
 这些事件的事件处理程序具有以下两个参数：  
  
|Parameter|描述|  
|---------------|--------|  
|*sender*|一个 <xref:System.Object>，表示引发事件的控件。|  
|*e*|一个包含 <xref:Microsoft.Office.Core.IRibbonControl> 的 <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>。  使用此控件可访问在 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 提供的功能区对象模型中不可用的任何属性。|  
  
## 请参阅  
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能区概述](../vsto/ribbon-overview.md)   
 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：在运行时更新功能区上的控件](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何：自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何：向 Backstage 视图添加控件](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：将功能区从功能区设计器导出为功能区 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：显示外接程序用户界面错误](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  