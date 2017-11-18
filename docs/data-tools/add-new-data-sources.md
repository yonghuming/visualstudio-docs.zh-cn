---
title: "将新数据源添加 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0c83367d383ab72194e5f83609b0f93d8602fdcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="add-new-data-sources"></a>添加新数据源
在 Visual Studio 中的.NET data tools 的上下文中术语*数据源*指连接到数据存储和公开到.NET 应用程序的数据的.NET 对象。 Visual Studio 设计器可以使用数据源生成将数据绑定到窗体中，当拖放中的数据库对象的样板文件代码的输出**数据源**窗口。 此类数据源可以是：  
  
-   与某种类型的数据库相关联的实体框架模型中的类。  
  
-   一个与某种类型的数据库相关联的数据集。  
  
-   一个表示 Windows Communication Foundation (WCF) 数据服务或 REST 服务之类的网络服务的类。  
  
-   一个表示 SharePoint 服务的类。  
  
-   类或你的解决方案中的集合。  
  
> [!NOTE]
>  如果你不使用数据绑定功能，则不适用于数据集、 实体框架中，LINQ to SQL，WCF 或 SharePoint，"数据源"的概念。 只需直接连接到数据库的使用 SQLCommand 对象，然后直接与数据库通信。  
  
 创建和编辑数据源使用**数据源配置向导**在 Windows 窗体或 Windows Presentation Foundation 应用程序。 用于实体框架，首先创建实体类，，，然后启动向导，通过选择**项目** > **添加新数据源**（本文后面的更多详细信息中所述）。  
  
 ![数据源配置向导](../data-tools/media/data-source-configuration-wizard.png "数据源配置向导")  
  
 创建数据源后，它将出现在**数据源**工具窗口 (Shift + Alt + D 或**视图** > **其他窗口** >  **数据源**)。 你可以将数据源从**数据源**窗口拖到窗体设计图面或控件。 这将导致样板文件代码以生成 — 显示起源于用户的数据存储区的数据的代码。 下图显示具有已放到 Windows 窗体的数据集。 如果你在应用程序上选择 F5，基础数据库中的数据将出现在窗体的控件。  
  
 ![数据源拖动操作](../data-tools/media/raddata-data-source-drag-operation.png "raddata 数据源拖动操作")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>数据库或数据库文件的数据源  
  
### <a name="dataset"></a>数据集  
 若要创建数据集作为数据源，运行**数据源配置向导**(**项目** > **添加新数据源**)，然后选择**数据库**数据源类型。 按照提示操作以指定新的或现有的数据库连接或数据库文件。  
  
### <a name="entity-classes"></a>实体类  
 若要创建的实体框架模型作为数据源，第一次运行**实体数据模型向导**创建实体类 (**项目** > **添加新项** >  **ADO.NET 实体数据模型**)。  
  
 ![新的实体框架模型项目项](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata 新实体框架模型项目项")  
  
 选择你想要生成模型所依据的方法。  
  
 ![实体数据模型向导](../data-tools/media/raddata-entity-data-model-wizard.png "raddata 实体数据模型向导")  
  
 添加模型作为数据源。 生成的类显示在**数据源配置向导**时选择**对象**类别。  
  
 ![与实体类的数据源配置向导](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata 与实体类的数据源配置向导")  
  
## <a name="data-source-for-a-service"></a>服务的数据源  
 若要从服务中创建数据源，运行**数据源配置向导**选择**服务**数据源类型。 这是实际上只是快捷方式**添加服务引用**对话框中，你还可以通过右键单击项目中的访问**解决方案资源管理器**并选择**添加服务引用**.  
  
 在从服务中创建数据源，Visual Studio 将添加到你的项目的服务引用。 Visual Studio 还会创建对应于该服务返回的对象的代理对象。 例如，返回的数据集的服务都在你的项目作为数据集;返回在项目中，作为类型中表示特定类型返回的一种服务。  
  
 你可以从以下类型的服务创建数据源：  
  
-   WCF 数据服务。 有关详细信息，请参阅[概述](/dotnet/framework/data/wcf/wcf-data-services-overview)。  
  
-   WCF 服务。 有关详细信息，请参阅[Windows Communication Foundation 服务和 Visual Studio 中的 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)。  
  
-   Web 服务。  
  
    > [!NOTE]
    >  在显示的项**数据源**窗口是依赖于该服务返回的数据。 某些服务可能没有提供足够的信息供**数据源配置向导**创建可绑定的对象。 例如，如果该服务返回一个非类型化数据集，则没有项将显示在**数据源**窗口在完成向导。 这是因为非类型化数据集不提供架构，并且因此向导没有足够的信息来创建数据源。  
  
## <a name="data-source-for-an-object"></a>对象的数据源  
 你可以从任何通过运行公开一个或多个公共属性的对象创建数据源**数据源配置向导**，然后选择**对象**数据源类型。 对象的所有公共属性显示在**数据源**窗口。   如果你使用实体框架，并且已生成一个模型，这是在哪里找到将你的应用程序的数据源的实体类。  
  
 上**选择数据对象**页上，展开树视图，找到你想要将绑定到的对象中的节点。 树视图包含节点为你的项目和程序集和你的项目引用的其他项目。  
  
 如果你想要将绑定到一个程序集或未显示在树视图中的项目中的对象，请单击**添加引用**并用**添加引用对话框**以添加对程序集或项目的引用。 添加引用后，程序集或项目添加到树视图。  
  
> [!NOTE]
>  你可能需要生成项目之前在树视图中显示这些对象包含你的对象。  
  
> [!NOTE]
>  若要支持拖放数据绑定对象实现<xref:System.ComponentModel.ITypedList>或<xref:System.ComponentModel.IListSource>接口必须具有默认构造函数。 否则为 Visual Studio 无法实例化的数据源对象，并且它将显示错误，当你将项拖动到设计图面。  
  
## <a name="data-source-for-a-sharepoint-list"></a>SharePoint 列表的数据源  
 你可以从 SharePoint 列表创建数据源，通过运行**数据源配置向导**并选择**SharePoint**数据源类型。 SharePoint 将数据通过公开[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]，因此创建 SharePoint 数据源是从服务中创建数据源相同。 选择**SharePoint**中项**数据源配置向导**打开**添加服务引用**对话框中，连接到 SharePoint 数据服务的位置通过指向 SharePoint 服务器。  这要求 SharePoint SDK。  
  
## <a name="see-also"></a>另请参阅  
 [适用于 NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)