---
title: "如何：将数据集和 TableAdapter 分离到不同的项目中 | Microsoft Docs"
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
  - "n 层应用程序, 分离数据集和 TableAdapter"
  - "TableAdapter, n 层应用程序"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将数据集和 TableAdapter 分离到不同的项目中
类型化数据集经过改进，现在可以在不同的项目中生成 [TableAdapter](../Topic/TableAdapters.md) 和数据集类。  这使您可以快速分离各应用程序层及生成 n 层数据应用程序。  
  
 下面的过程介绍使用[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)在项目中生成数据集代码的步骤，此项目不同于包含所生成的 `TableAdapter` 代码的项目。  
  
## 分离数据集和 TableAdapter  
 将数据集代码与 `TableAdapter` 代码分离时，要包含数据集代码的项目必须位于当前解决方案中。  如果此项目不在当前解决方案中，则**“属性”**窗口的**“数据集项目”**列表中不会列出该项目。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 将数据集分离到不同的项目中  
  
1.  打开包含数据集（.xsd 文件）的解决方案。  
  
    > [!NOTE]
    >  如果解决方案中不包含要将数据集代码分离到的项目，请创建该项目，或将现有项目添加到解决方案中。  
  
2.  在**“解决方案资源管理器”**中，双击类型化数据集文件（.xsd 文件），以在**“数据集设计器”**中打开该数据集。  
  
3.  单击**“数据集设计器”**的空白区域。  
  
4.  在**“属性”**窗口中查找**“数据集项目”**节点。  
  
5.  在**“数据集项目”**列表中，单击要在其中生成数据集代码的项目的名称。  
  
     单击要在其中生成数据集代码的项目后，**“数据集文件”**属性将填充默认文件名。  如果需要，可以更改此名称。  此外，如果要在特定目录中生成数据集代码，可将**“项目文件夹”**属性设置为文件夹的名称。  
  
    > [!NOTE]
    >  分离数据集与 TableAdapter 时（通过设置**“数据集项目”**属性），将不会自动移动项目中现有的数据集分部类。  您必须手动将它们移到数据集项目中。  
  
6.  保存数据集。  
  
     数据集代码将在**“数据集项目”**属性中选定的项目中生成，在当前项目中生成**“TableAdapter”**代码。  
  
 默认情况下，分离数据集和 `TableAdapter` 代码后，每个项目中将包含一个独立的类文件。  原始项目将包含一个名为 DatasetName.Designer.vb（或 DatasetName.Designer.cs）的文件，其中含有 `TableAdapter` 代码。  **“数据集项目”**属性中指定的项目将包含一个名为 DatasetName.DataSet.Designer.vb（或 DatasetName.DataSet.Designer.cs）的文件，其中含有数据集代码。  
  
> [!NOTE]
>  选定数据集或 `TableAdapter` 项目后，在**“解决方案资源管理器”**中单击**“显示所有文件”**可查看生成的类文件。  
  
## 请参阅  
 [N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)   
 [演练：创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [分层更新](../data-tools/hierarchical-update.md)   
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)