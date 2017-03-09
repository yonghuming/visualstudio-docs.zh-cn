---
title: "如何：在 Visual Studio 中将 WPF 控件绑定到数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [WPF], 显示"
  - "数据绑定, WPF"
  - "显示数据, WPF"
  - "WPF [WPF], 数据"
  - "WPF 数据绑定 [Visual Studio]"
  - "WPF 设计器, 数据绑定"
  - "WPF, Visual Studio 中的数据绑定"
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 Visual Studio 中将 WPF 控件绑定到数据
使用**“数据源”**窗口可以创建数据绑定 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 控件。  首先，将数据源添加到**“数据源”**窗口中。  然后，将项从**“数据源”**窗口拖动到**“WPF 设计器”**中。  
  
##  <a name="adding"></a> 将“数据源”添加到“数据源”窗口中  
 你必须先将数据源添加到**“数据源”**窗口中，然后才能创建数据绑定控件。  
  
#### 将数据源添加到“数据源”窗口中  
  
1.  在**“视图”**菜单上，指向**“其他窗口”**，然后单击**“数据源”**。  
  
2.  单击**“添加新数据源”**，然后完成**“数据源配置向导”**。  
  
3.  执行以下任务之一以创建数据绑定控件：  
  
    -   [创建绑定到单个数据字段的控件](#simple)。  
  
    -   [创建绑定到多个数据字段的控件](#complex)。  
  
    -   [创建一组绑定到多个数据字段的控件](#details)。  
  
    -   [在设计器中将数据绑定到现有控件](#existing)。  
  
##  <a name="simple"></a> 创建绑定到单个数据字段的控件  
 在将数据源添加到**“数据源”**窗口中后，你可以创建显示单个数据字段的新的数据绑定控件，例如 <xref:System.Windows.Controls.ComboBox> 或 <xref:System.Windows.Controls.TextBox>。  
  
#### 创建绑定到单个数据字段的控件  
  
1.  在**“数据源”**窗口中，展开一个表示表或对象的项。  查找表示要绑定到的列或属性的子项。  有关可视示例，请参阅[“数据源”窗口](../Topic/Data%20Sources%20Window.md)。  
  
2.  （可选）选择要创建的控件。  **“数据源”**窗口中的每个项都具有一个默认控件，当你将该项拖动到设计器中时，将会创建该控件。  默认控件将取决于项的基础数据类型。  
  
     若要选择一个不同的控件，请单击项旁边的下拉箭头，然后选择一个控件。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
3.  在设计器中将项拖动到有效容器（例如 <xref:System.Windows.Controls.Grid>）中。  有关有效容器的详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将在容器中创建新的数据绑定控件和一个带有适当标题的 <xref:System.Windows.Controls.Label>。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 还会生成 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 和代码以将控件绑定到数据。  有关详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
##  <a name="complex"></a> 创建绑定到多个数据字段的控件  
 在将数据源添加到**“数据源”**窗口中后，你可以创建显示多个数据字段的新的数据绑定控件，例如 <xref:System.Windows.Controls.DataGrid> 或 <xref:System.Windows.Controls.ListView>。  
  
#### 创建绑定到多个数据字段的控件  
  
1.  在**“数据源”**窗口中，选择一个表示表或对象的项。  有关可视示例，请参阅[“数据源”窗口](../Topic/Data%20Sources%20Window.md)。  
  
2.  （可选）选择要创建的控件。  默认情况下，**“数据源”**窗口中每个表示数据表或对象的项都将设置为创建 <xref:System.Windows.Controls.DataGrid>（如果项目针对的是 .NET Framework 4）或 <xref:System.Windows.Controls.ListView>（对于早期版本的 .NET Framework）。  
  
     若要选择一个不同的控件，请单击项旁边的下拉箭头，然后选择一个控件。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果你不希望显示特定的列或属性，请展开该项以显示其子级。  单击你不希望显示的列或属性旁边的下拉箭头，然后单击**“无”**。  
  
3.  在设计器中将项拖动到有效容器（例如 <xref:System.Windows.Controls.Grid>）中。  有关有效容器的详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会在容器中创建新的数据绑定控件。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 还会生成 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 和代码以将控件绑定到数据。  有关详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
##  <a name="details"></a> 创建一组绑定到多个数据字段的控件  
 在将数据源添加到**“数据源”**窗口中后，你可以将数据表或对象绑定到一组控件。  这将为表或对象中的每个列或属性创建一个不同的控件。  
  
#### 创建一组绑定到多个数据字段的控件  
  
1.  在**“数据源”**窗口中，选择一个表示表或对象的项。  有关可视示例，请参阅[“数据源”窗口](../Topic/Data%20Sources%20Window.md)。  
  
2.  单击项旁边的下拉箭头，然后选择**“详细信息”**。  
  
    > [!NOTE]
    >  如果你不希望显示特定的列或属性，请展开该项以显示其子级。  单击你不希望显示的列或属性旁边的下拉箭头，然后单击**“无”**。  
  
3.  在设计器中将项拖动到有效容器（例如 <xref:System.Windows.Controls.Grid>）中。  有关有效容器的详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会在容器中创建新的数据绑定控件。  每个控件都将绑定到一个不同的列或属性，并且每个控件都对应有一个具有适当标题的 <xref:System.Windows.Controls.Label> 控件。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 还会生成 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 和代码以将控件绑定到数据。  有关详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
##  <a name="existing"></a> 在设计器中将数据绑定到现有控件  
 在将数据源添加到**“数据源”**窗口中后，你可以在设计器中将数据绑定添加到现有控件。  
  
#### 在设计器中将数据绑定到现有控件  
  
1.  在**“数据源”**窗口中，使用以下过程之一：  
  
    -   若要将数据绑定添加到显示多个数据字段的现有控件（例如 <xref:System.Windows.Controls.DataGrid> 或 <xref:System.Windows.Controls.ListView>），请选择表示要绑定到该控件的表或对象的项。  
  
    -   若要将数据绑定添加到显示单个数据字段的现有控件（例如 <xref:System.Windows.Controls.ComboBox> 或 <xref:System.Windows.Controls.TextBox>），请展开表示包含数据的表或对象的项，然后选择表示要绑定到该控件的数据的项。  
  
2.  将选定的项从**“数据源”**窗口拖动到设计器中的现有控件上。  该控件必须是有效的放置目标。  有关详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会生成 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 和代码以将控件绑定到数据。  有关详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
    > [!NOTE]
    >  如果该控件已绑定到数据，则会将该控件的数据绑定重置为最近拖动到该控件上的项。  
  
## 请参阅  
 [在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：在 WPF 应用程序中创建查找表](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [如何：在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)   
 [演练：将 WPF 控件绑定到数据集](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [演练：将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [演练：在 WPF 应用程序中显示相关数据](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)