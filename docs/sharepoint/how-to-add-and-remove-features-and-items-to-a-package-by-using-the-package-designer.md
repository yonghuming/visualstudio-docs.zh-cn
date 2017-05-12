---
title: "如何：使用包设计器在包中添加和移除功能和项 | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.PackageDesignerDesign"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 包"
ms.assetid: 7dfa2c5d-3ac7-4573-abac-12a5e16efd1d
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：使用包设计器在包中添加和移除功能和项
  在创建 SharePoint 解决方案时，Visual Studio 会向解决方案中的包添加默认 SharePoint 功能。  在最终部署之前，可以添加和移除 SharePoint 项目项和功能以修改 SharePoint 包。  
  
 或者，可以使用打包资源管理器来添加和移除 SharePoint 项目项。  也可以查看和更改放置到包 \(.wsp\) 中的 SharePoint 项目项和功能的层次结构。  有关详细信息，请参阅[如何：使用打包资源管理器在包中添加和移除功能和项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
## 向 SharePoint 包添加功能  
 可以使用包设计器向 SharePoint 包添加功能。  
  
#### 使用包设计器添加 SharePoint 功能  
  
1.  打开**“包设计器”**。  
  
     有关详细信息，请参阅[如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  通过执行以下一个或多个步骤添加一个或多个 SharePoint 功能：  
  
    1.  双击要添加的 **解决方案中的项** 列表的每一项。  
  
    2.  选择要添加的项，然后选择 **添加** 按钮 \(\>\)。  
  
    3.  选择 **全部添加** 按钮 \(\>\>\) 立即添加所有项。  
  
     例如，可以双击**“解决方案中的项”**列表中的一个项以将该项添加到**“包中的项”**列表中。  
  
     SharePoint 项目项和功能将出现在**“包中的项”**列表中。  
  
## 从 SharePoint 包中移除功能  
 可以使用包设计器从 SharePoint 包中移除功能。  
  
#### 使用包设计器移除 SharePoint 功能  
  
1.  在 **包中的项** 列表中，选择要删除的项，然后选择 **移除** \(\<\) 按钮或选择 **全部移除** 按钮 \(\<\<\) 移除所有项。  
  
     SharePoint 项将出现在**“解决方案中的项”**列表中。  
  
## 请参阅  
 [创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [NOT IN BUILD: How to: Modify Package Properties](http://msdn.microsoft.com/zh-cn/372089ce-cda9-4c21-beb2-f964990b96ee)   
 [How to: Create a Package](http://msdn.microsoft.com/zh-cn/b24be45c-e91d-49bb-afb0-7b265404214b)  
  
  