---
title: "在 N 层应用程序中使用数据集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - "数据 [Visual Basic], n 层应用程序"
  - "数据集项目 [VS n 层应用程序]"
  - "数据集 [Visual Basic], n 层应用程序"
  - "分布式应用程序 [VS n 层应用程序]"
  - "多层应用程序"
  - "多层数据库应用程序"
  - "n 层应用程序"
  - "TableAdapter, n 层应用程序"
  - "层, n 层应用程序"
  - "类型化数据集, n 层应用程序"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 N 层应用程序中使用数据集
*“N 层数据应用程序”*是以数据为中心且分为多个逻辑层（或*“多层”*）的应用程序。  换句话说，N 层数据应用程序是分离到多个项目中的应用程序，数据访问层、业务逻辑层和表示层都在各自的项目中。  有关详细信息，请参阅[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)。  
  
 类型化数据集经过改进，现在可以在相互独立的项目中生成 TableAdapter 和数据集类。  这使你可以快速分离各应用程序层及生成 N 层数据应用程序。  
  
 类型化数据集对 N 层的支持，使应用程序体系结构的迭代开发可以采取 N 层设计，并免除了手动将代码分离到多个项目中。  设计数据层从使用[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)开始。  如果你已准备好对应用程序体系结构采用 N 层设计，请设置数据集的**“数据集项目”**属性，以在另一个项目中生成数据集类。  
  
## 本节内容  
 [如何：将数据集和 TableAdapter 分离到不同的项目中](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 介绍如何将生成的数据集类移出包含生成的 TableAdapter 类的项目，并移入新的项目中。  
  
 [如何：向 N 层应用程序中的 TableAdapter 添加代码](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 介绍如何生成可以在其中为 N 层 TableAdapter 添加代码的分部类。  
  
 [如何：向 N 层应用程序的数据集添加代码](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 介绍如何生成可以在其中为 N 层数据集添加代码的分部类。  
  
 [如何：向 N 层数据集添加验证](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 介绍添加对更改数据执行验证的代码的位置。  
  
 [演练：创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 提供有关创建类型化数据集并将 TableAdapter 和数据集代码分离到多个项目中的分步说明。  
  
 [演练：向 N 层数据应用程序添加验证](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 提供有关将验证添加到在 N 层数据应用程序演练中创建的应用程序的分步说明。  
  
## 参考  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## 相关章节  
 [N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)  
  
 [分层更新](../data-tools/hierarchical-update.md)  
  
 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)  
  
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)  
  
 [使用 LINQ to SQL 的 N 层应用程序和远程应用程序](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)