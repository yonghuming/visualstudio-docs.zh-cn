---
title: "数据源概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], 数据源"
  - "数据源"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据源概述
数据源表示可用于应用程序的数据。  更具体而言，数据源表示您希望在应用程序中使用的数据。  数据源可从数据库（包括本地数据库文件）、服务以及对象中获得。  
  
 您添加到项目的数据源显示在**“数据源”**窗口中。  在许多情况下，您可以将数据源拖到 Windows 窗体、WPF 和 Silverlight 设计器来创建绑定到基础数据的控件。  有关详细信息，请参阅 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
 Visual Studio 提供用于创建和编辑应用程序中的数据源的工具。  根据从基础数据存储区返回的对象，Visual Studio 项目中的数据源可表示为实体数据模型、数据集、服务返回的代理对象或其他对象类型。  
  
 您将使用**“数据源配置向导”**创建和编辑数据源。  
  
## 从数据库创建的数据源  
 通过运行**“数据源配置向导”**并选择**“数据库”**数据源类型，可以从数据库创建数据源。  有关详细信息，请参阅 [如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)。  
  
 在从数据库创建数据源时，Visual Studio 将生成一个数据模型并将其添加到项目。  数据模型是数据库基础数据的强类型可编程视图。  可以使用 Visual Studio 创建以下类型的数据模型：  
  
-   基于[实体数据模型](../Topic/Entity%20Data%20Model.md)的概念模型。  此类型的模型可由实体框架或 WCF 数据服务使用。  有关更多信息，请参见[实体框架概述](../Topic/Entity%20Framework%20Overview.md)和[WCF 数据服务 4.5](../Topic/WCF%20Data%20Services%204.5.md)。  
  
-   类型化数据集。  有关详细信息，请参阅 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
-   LINQ to SQL 类。  有关详细信息，请参阅 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)。  
  
    > [!NOTE]
    >  与基于实体数据模型的概念模型和数据集不同，不能使用**“数据源配置向导”**来创建 LINQ to SQL 类。  这些类也不会出现在**“数据源”**窗口中，因此无法将它们拖到设计器中来创建数据绑定控件。  不过，您可以创建基于 LINQ to SQL 类的对象数据源，然后将这些对象拖到设计器中。  有关详细信息，请参阅 [如何：创建映射到表和视图的 LINQ to SQL 类（O\/R 设计器）](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)。  
  
### 从本地数据库文件创建的数据源  
 您还可以从以下类型的数据库文件创建数据源：Access 数据库（.mdb 文件）、SQL Server Express LocalDB 数据库（.mdf 文件）和 SQL Server Express 数据库（.mdf 文件）。  在从这些数据库文件创建数据源时，您可以将数据库文件直接添加到项目。  有关更多信息，请参见下列主题：  
  
-   [本地数据概述](../data-tools/local-data-overview.md)  
  
-   [如何：管理项目中的本地数据文件](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
## 从服务创建的数据源  
 通过运行**“数据源配置向导”**并选择**“服务”**数据源类型，可以从服务创建数据源。  有关详细信息，请参阅 [如何：连接到服务中的数据](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
 在从服务创建数据源时，Visual Studio 会向项目中添加一个服务引用。  Visual Studio 还会创建与服务返回的对象对应的代理对象。  例如，返回数据集的服务在项目中表示为数据集；返回特定类型的服务在项目中表示为所返回的类型。  
  
 可以从以下类型的服务创建数据源：  
  
-   WCF 数据服务。  有关详细信息，请参阅 [概述](../Topic/WCF%20Data%20Services%20Overview.md)。  
  
-   Windows Communication Foundation \(WCF\) 服务。  有关详细信息，请参阅 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)。  
  
-   Web 服务。  有关详细信息，请参阅 [使用托管代码进行 Web 服务编程简介](http://msdn.microsoft.com/zh-cn/bd8861f3-39e1-4c06-995e-677e007eb961)。  
  
    > [!NOTE]
    >  **“数据源”**窗口中显示的项取决于服务返回的数据。  某些服务可能没有为**“数据源配置向导”**创建可绑定的对象提供足够的信息。  例如，如果服务返回一个非类型化数据集，则向导完成时**“数据源”**窗口中将不会出现任何项。  这是因为非类型化数据集不提供架构，因此该向导没有足够的信息来创建数据源。  
  
## 从对象创建的数据源  
 通过运行**“数据源配置向导”**然后选择**“对象”**数据源类型，可以从公开一个或多个公共属性的任何对象创建数据源。  对象的所有公共属性显示在**“数据源”**窗口中。  有关详细信息，请参阅 [如何：连接到对象中的数据](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)。  
  
 有关绑定到对象的更多信息，请参见 [Visual Studio 中的对象绑定](../data-tools/bind-objects-in-visual-studio.md)。  
  
## 从 SharePoint 列表创建的数据源  
 通过运行**“数据源配置向导”**并选择**“SharePoint”**数据源类型，可以从 SharePoint 列表创建数据源。  SharePoint 通过 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]公开数据，因此创建 SharePoint 数据源的过程与从服务创建数据源相同。  在**“数据源配置向导”**中选择**“SharePoint”**项将打开**“添加服务引用”**对话框，您将在该对话框中通过指向 SharePoint 服务器来连接到 SharePoint 数据服务。  有关详细信息，请参阅 [如何：连接到服务中的数据](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
## 请参阅  
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [“数据源”窗口](../Topic/Data%20Sources%20Window.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)