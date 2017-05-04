---
title: "如何：使用模块包括文件 | Microsoft Docs"
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
  - "模块 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 模块"
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：使用模块包括文件
  模块（不要与 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 模块混淆）是一些容器，您可以利用它们将诸如 ASPX 母版页、文本文件或图像部署到 SharePoint。  
  
 可以选择将文件部署到文档库或作为普通文件（例如，default.aspx）部署在文档库的外部。  若要将文件添加到文档库，请指定 `Type="GhostableInLibrary"` 作为 **File** 元素中的特性。  此设置指示 SharePoint 创建要在将文件添加到库时随文件一起添加的列表项。  若要将文件部署在文档库的外部，请指定 `Type="Ghostable"`，或只需忽略 **Type** 特性。  
  
## 向 SharePoint 解决方案中添加模块  
  
#### 添加模块  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中打开或创建一个 SharePoint 项目。  
  
     有关详细信息，请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在**“解决方案资源管理器”**中，选择项目节点，然后在菜单栏上选择**“项目”**，再选择**“添加新项”**。  
  
     **“添加新项”**对话框打开。  
  
3.  在SharePoint模板列表中，选择“模型”模板，然后选择“添加”按钮。  
  
     这将在项目中创建一个名为 Module1 的节点。  
  
4.  在 Module1 下，移除 Sample.txt 文件。  
  
     Sample.txt 包括在所有新模块中作为示例，并且不是必需的。（请注意，如果删除该文件，则还会从模块的 Elements.xml 文件中移除该文件的项。）  
  
5.  如果希望文件部署到 SharePoint 中的特定文件夹结构，请在 Module1下的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 通过选择 Module1 节点创建这些文件夹 ，然后，菜单栏上，选择 ”项目“，选择 ”新建文件夹“。  
  
6.  选择要在其中添加文件的文件夹，然后在菜单栏上，选择“项目”，添加现有项”。  
  
7.  选择一个或多个要部署到 SharePoint 的文件，然后单击“添加”。  
  
     将文件添加到项目时，会自动将该文件的项添加到模块的 Elements.xml 文件。  在部署项目时，会将文件复制到 SharePoint 服务器相对于项目的根目录的位置，该位置由 **File** 元素的 **Url** 特性指定，例如 `Url="Module1/New Folder/SomeFile.doc`。  如果要更改文件的部署位置，请在**“解决方案资源管理器”**中将其移到另一个文件夹，或更改其 **Url** 设置。  
  
8.  对于希望出现在文档库中的任何文件，请将 `Type="GhostableInLibrary"` 特性追加到这些文件在 Elements.xml 中的项。  例如，  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. 部署项目。  
  
     文件复制到 SharePoint 中的指定位置。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  