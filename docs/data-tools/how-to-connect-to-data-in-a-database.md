---
title: "如何：连接到数据库中的数据 | Microsoft Docs"
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
  - "数据 [Visual Studio], 连接到数据库"
  - "数据源, 创建"
  - "数据源, 数据库"
  - "数据库连接"
  - "数据库, 连接"
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
caps.handback.revision: 55
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：连接到数据库中的数据
你可以使用 Visual Studio 将应用程序连接到数据库。  创建数据连接后，Visual Studio 将生成一个数据模型，应用程序将使用该数据模型与数据库中的数据交互。  数据模型中的对象显示在[“数据源”窗口](../Topic/Data%20Sources%20Window.md)中。  然后，你可以通过将项从**“数据源”**窗口拖到设计图面来创建数据绑定控件。  有关详细信息，请参阅[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
 本主题提供有关连接到数据库和创建以下类型的数据模型的说明：  
  
-   数据集  
  
-   实体数据模型 \(EDM\)  
  
> [!NOTE]
>  也可以使用 Visual Studio 通过数据库创建 LINQ to SQL 类。  但是，LINQ to SQL 类不会显示在**“数据源”**窗口中，因此无法直接将该类拖到设计器中来创建数据绑定控件。  有关通过数据库创建 LINQ to SQL 类的详细信息，请参阅[如何：创建映射到表和视图的 LINQ to SQL 类（O\/R 设计器）](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
##  <a name="dataset"></a> 连接到数据库并创建数据集  
 当你创建基于数据库的数据集时，Visual Studio 将创建一组表示数据的可编程视图的类。  主类称为“类型化数据集”。  类型化数据集包含表示数据库中的表的数据表对象。  有关类型化的数据集的详细信息，请参阅 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
 创建数据集后，你可以通过将数据集对象从“数据源”窗口拖到 WPF 或 Windows 窗体设计器来创建数据绑定 WPF 或 Windows 窗体控件。  
  
#### 将应用程序连接到数据库并创建数据集  
  
1.  在 Visual Studio 中打开一个现有项目，或创建一个新项目。  
  
2.  在**“数据”**菜单上，单击**“添加新数据源”**。  
  
     **“数据源配置向导”**打开。  
  
3.  在**“选择数据源类型”**页上，选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择数据库模型”**页上，选择**“数据集”**，然后单击**“下一步”**。  
  
5.  在**“选择你的数据连接”**页上，从可用连接的列表中选择一个数据连接，然后单击**“下一步”**。  
  
     如果所需的数据连接不可用，请通过执行[创建新数据库连接](#CreatingDataConnection)中的步骤创建一个新连接。  
  
6.  在**“将连接字符串保存到应用程序配置文件中”**页上，如果要将连接字符串直接保存在编译的应用程序中，请选择性地清除**“是，将连接另存为”**复选框。  默认情况下，连接保存在应用程序配置文件中。  有关详细信息，请参阅[如何：保存和编辑连接字符串](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md)。  
  
7.  在**“选择数据库对象”**页上，选择将在应用程序中使用的数据库对象。  你还可以选择替换默认的**“DataSet 名称”**。  
  
8.  单击**“完成”**。  刚刚创建的数据集即出现在**“数据源”**窗口中。  
  
    > [!NOTE]
    >  如果**“数据源”**窗口未打开，请在**“数据”**菜单上，单击**“显示数据源”**以打开该窗口。  
  
9. 现在，你可以将项从**“数据源”**窗口拖到 WPF 设计器、Windows 窗体设计器或[Component Designer](../Topic/Component%20Designer.md)来创建数据绑定控件。  有关详细信息，请参阅[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
##  <a name="edm"></a> 连接到数据库并创建实体数据模型  
 当你创建基于数据库的实体数据模型时，Visual Studio 将创建一组表示数据的可编程视图的类。  有关实体数据模型和 ADO.NET Entity Framework 的详细信息，请参阅[实体框架概述](../Topic/Entity%20Framework%20Overview.md)。  
  
 创建实体数据模型后，你可以通过将实体对象从“数据源”窗口拖到 WPF 设计器来创建数据绑定 WPF 控件。  
  
#### 将应用程序连接到数据库并创建实体数据模型  
  
1.  在 Visual Studio 中打开一个现有项目，或创建一个新项目。  
  
2.  按照**“实体数据模型向导”**中的步骤进行操作，以连接到数据库并指定模型的内容。  有关详细信息，请参阅[How to: Create a New .edmx File](http://msdn.microsoft.com/zh-cn/beb8189e-e51c-4051-839c-9902c224abf2)。  
  
3.  完成**“实体数据模型向导”**后，你创建的实体数据模型将在实体数据模型设计器中打开，并且现在即可在**“数据源”**窗口中找到数据对象。  
  
    > [!NOTE]
    >  如果**“数据源”**窗口未打开，请在**“数据”**菜单上，单击**“显示数据源”**以打开该窗口。  
  
4.  如果 WPF 设计器处于打开状态，你现在可以将项从**“数据源”**窗口拖到设计器来创建绑定到实体数据模型的控件。  有关详细信息，请参阅[如何：在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)。  
  
     如果 Windows 窗体设计器处于打开状态，你无法将项从**“数据源”**拖到设计器。  若要创建绑定到实体数据模型的控件，你必须生成项目，添加基于实体数据模型的新对象数据源，然后将这些对象拖到设计器。  
  
##  <a name="CreatingDataConnection"></a> 创建新数据库连接  
 在使用**“数据源配置向导”**或**“实体数据模型向导”**时，你必须指定要使用的数据库连接。  如果还没有数据库连接，请执行以下步骤创建连接。  
  
 这些说明假定你已按[连接到数据库并创建数据集](#dataset)和[连接到数据库并创建实体数据模型](#edm)中所述的方式启动了**“数据源配置向导”**或**“实体数据模型向导”**。  
  
#### 创建新数据库连接  
  
1.  在**“数据源配置向导”**或**“实体数据模型向导”**的**“选择你的数据连接”**页上，单击**“新建连接”**。  
  
     将进行以下操作之一：  
  
    -   如果已在 Visual Studio 中创建了数据连接，则**“添加连接”**对话框将打开。  
  
    -   如果此连接是你在 Visual Studio 中创建的第一个数据连接，则**“选择数据源”**对话框将显示。  选择要连接到的数据库的类型，然后单击**“确定”**显示**“添加连接”**对话框。  
  
2.  在**“添加连接”**对话框中，输入请求的信息。  每种类型的数据提供程序的**“添加连接”**对话框都不同。  
  
    > [!NOTE]
    >  如果你在**“添加连接”**对话框中选择的**“数据源”**不是要连接到的数据源，请单击**“更改”**打开**“更改数据源”**对话框，然后选择其他数据源。  
  
3.  在**“添加连接”**对话框中，单击**“确定”**。  
  
     将返回到**“数据源配置向导”**或**“实体数据模型向导”**的**“选择你的数据连接”**页。  
  
4.  在**“选择你的数据连接”**页上，确保新的数据连接处于选定状态，然后单击**“下一步”**。  
  
5.  完成**“数据源配置向导”**或**“实体数据模型向导”**中的其余步骤。  
  
## .NET Framework 安全性  
 存储敏感信息（如密码）会影响应用程序的安全性。  若要控制对数据库的访问，一种较为安全的方法是使用 Windows 身份验证（也称为集成安全性）。  有关详细信息，请参阅[保护连接信息](../Topic/Protecting%20Connection%20Information.md)。  
  
## 请参阅  
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [连接到数据源](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)