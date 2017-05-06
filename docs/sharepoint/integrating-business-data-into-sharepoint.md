---
title: "将业务数据集成到 SharePoint 中"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], 聚合数据"
  - "BDC [Visual Studio 中的 SharePoint 开发], 业务数据"
  - "BDC [Visual Studio 中的 SharePoint 开发], 创建模型"
  - "BDC [Visual Studio 中的 SharePoint 开发], 数据"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 聚合数据"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 业务数据"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 创建模型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 数据"
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 将业务数据集成到 SharePoint 中
  可以将业务数据集成到 SharePoint 中。  业务数据可能来自后端服务器应用程序，如 [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]、Siebel 和 SAP，或来自 Web 服务。  通过使用 SharePoint 中的外部列表或业务数据 Web 部件，用户可以查看、添加、更新或删除业务数据。用户还可以在 Microsoft Office 应用程序（例如 Microsoft Outlook）中脱机访问此数据。  有关更多信息，请参见[此处可以显示外部数据](http://go.microsoft.com/fwlink/?LinkId=169295)。  
  
 若要将数据集成到 SharePoint 中，请创建业务数据连接 \(BDC\) 服务的模型。  BDC 服务是 SharePoint 中的一个应用程序，存储有关业务应用程序中数据的信息。  有关更多信息，请参见 [业务数据连接\(BDC\) 服务](http://go.microsoft.com/fwlink/?LinkID=169276)。  
  
## Visual Studio 中的模型  
 借助于 Visual Studio 中的模型，您可以编写自定义代码以检索和更新来自后端数据源的数据。  您还可以聚合来自多个数据源的数据。  例如，可以显示包含来自 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] 数据库和 Web 服务的数据的客户列表。  
  
 还可以导入已部署到 SharePoint 中的模型。  导入模型之后，您可以添加自定义代码，也可以只使用 Visual Studio 来打包模型，并将其部署到多个 SharePoint Server 服务器场。  有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## 在 Visual Studio 中设计模型  
 可以通过使用设计器和一些工具窗口来设计模型。  当您设计模型时，Visual Studio 将会生成模型 XML。  有关详细信息，请参阅[BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
 模型中包含实体和方法。  
  
### 实体  
 一个实体描述一个字段集合。  例如，实体可以表示数据库中的表。  实体作为 SharePoint 中的外部内容类型出现。  有关外部内容类型的更多信息，请参见 [什么是外部内容类型？](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### 方法  
 外部内容类型的使用者可以使用方法来对实体的字段执行操作。  例如，用户可以利用 Updater 方法来更改客户的地址和出生日期，其中 `Address` 和 `BirthDate` 是 `Customer` 实体的字段。  
  
 Visual Studio 将会为模型中的每个实体都生成一个服务代码文件。  将方法添加到模型中时，Visual Studio 将在服务代码文件中生成对应的方法。  将代码添加到每个方法中即可执行相应的任务。  例如，如果将 Creator 方法添加到模型中，则 Visual Studio 将在服务代码文件中生成 Creator 方法。  当用户在基于模型的列表中单击**“新建项目”**按钮时，BDC 服务将调用此方法。  因此，应在 Creator 方法中添加向数据源添加新数据的代码。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)|演示如何创建新模型或导入从 SharePoint 导出的模型。|  
|[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)|说明如何使用 Visual Studio 设计工具设计模型的元素。|  
|[在使用 SharePoint Designer 与 Visual Studio，在生成解决方案时使用 BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|帮助您确定是使用 Visual Studio 还是使用 SharePoint Designer 来创建 BDC 模型。|  
  
  