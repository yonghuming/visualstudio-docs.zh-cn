---
title: "如何：使用打包资源管理器在包中添加和移除功能和项 | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.PackagingExplorer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 包"
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：使用打包资源管理器在包中添加和移除功能和项
  若要配置包以部署 SharePoint 项和功能，可以使用打包资源管理器。  可以在 .wsp 文件内调整 SharePoint 项目项和功能。  
  
 或者，可以使用打包设计器来查看功能并重新对其排序，以更改激活顺序。  有关详细信息，请参阅[如何：使用包设计器在包中添加和移除功能和项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。  
  
## 打开打包资源管理器  
 如果 Visual Studio 解决方案包含至少一个 SharePoint 项目，则可以使用以下过程打开打包资源管理器。  或者，当您查看某个功能或包设计器时，打包资源管理器将自动打开。  在关闭所有功能和包设计器后，打包资源管理器也将关闭。  
  
#### 打开打包资源管理器  
  
1.  在菜单栏上，依次选择**“视图”**、**“其他窗口”**和**“打包资源管理器”**。  
  
     **“打包资源管理器”**将出现在**“工具箱”**中。  
  
## 向包中添加功能  
 可以使用打包资源管理器向包中添加新功能和现有功能。  
  
#### 添加 SharePoint 功能  
  
1.  打开 **打包资源管理器**，打开项目的快捷菜单，然后选择 **添加功能**。  
  
#### 移动现有 SharePoint 功能  
  
1.  打开 **打包资源管理器**，然后执行下列步骤之一：  
  
    -   将**“功能”**从一个项目拖放到另一个项目中。  
  
    -   打开功能的快捷菜单，选择 **剪切**，打开要移动功能的项目的快捷菜单，然后选择 **粘贴**。  
  
    > [!NOTE]  
    >  如果解决方案中包含多个 SharePoint 项目，请使用此过程。  
  
## 验证功能或包  
 可以通过验证文件来找出 SharePoint 功能和包中可能存在的问题。  “输出”窗口和“错误列表”窗口中将显示警告和错误。  
  
#### 验证 SharePoint 功能或包  
  
1.  打开**“打包资源管理器”**。  
  
2.  打开功能设计器或包的快捷菜单，然后选择 **验证**。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  