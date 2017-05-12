---
title: "创建 SharePoint 的网站栏、内容类型和列表"
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
  - "VS.SharePointTools.ListDesigner.ContentTypeSetting"
  - "VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ListDesigner.CreatingLists"
  - "VS.SharePointTools.ListDesigner.ListPage"
  - "VS.SharePointTools.ListDesigner.ViewPage"
  - "VS.SharePointTools.ListDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ContentTypeDesigner.ColumnsPage"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 9ceed263-3aec-41dc-8708-63cb37a08fa8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 创建 SharePoint 的网站栏、内容类型和列表
  Visual Studio 提供许多不同的基本 SharePoint 项目项的项模板，包括 *列表*、*内容类型*，这两者均可合并网站栏 \(或 *字段*\)。  内容类型和列表的新设计器可更简单地创建这些项。  
  
## 网站栏  
 站点列是您可以向 SharePoint 项目添加的一种最基本元素。  网站栏表示数据的类型，就像电话号码，注释，或者在联系人的列表中的某一联系人的城市名称。  
  
 新网站栏项目项模板使创建网站列比在 Visual Studio 的早期版本更容易。  创建新网站栏之后，您可以修改在网站栏的 Elements.xml 文件的XML文件以包含您想要的信息，例如其显示名称，其数据类型和您希望网站显示在 SharePoint 中的列的组。  有关网站列的更多信息，请参见[列的简介](http://go.microsoft.com/fwlink/?LinkId=224996)。  
  
## 内容类型和列表  
 内容类型和列表是在 SharePoint 中常用的元素。  
  
 内容类型定义了SharePoint 列表或文档库中的元数据、工作流和项类别的行为。  例如，您可在联系人列表或任务列表，创建内容类型的信息。  联系人内容类型可以包含列，如用户名、电子邮件、电话号码和地址。  您定义站点级别的内容类型是网站中独立的任何列表或文档库。  在SharePoint 网站，您可以使用相同内容类型的不同列表或文档库。  您还可以使用同一列表或文档库关联的内容类型。  
  
 在SharePoint 中，列表是您分享给其他人的信息的集合。  列表由行包含数据列。  列表的一些示例包括：任务列表，联系人列表，和公告列表。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的新内容类型和列表设计器，使创建站点内容类型和列表比在 Visual Studio 的早期版本更容易、更直观。  UI 允许您一个熟悉情况下，以可视方式构造内容类型和列表，并可以在列表和使用组标题中排序和分组数据。  有关内容类型的更多信息，请参见[内容类型](http://go.microsoft.com/fwlink/?LinkId=224997)。  有关列表的更多信息，请参见[表格形式](http://go.microsoft.com/fwlink/?LinkId=224998) 和 [列表视图](http://go.microsoft.com/fwlink/?LinkId=224999)。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[演练：创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|演示如何创建自定义内容类型的网站栏。  内容类型随后用于自定义列表。|  
  
## 请参阅  
 [开发 SharePoint 2010 的 Get Started](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  