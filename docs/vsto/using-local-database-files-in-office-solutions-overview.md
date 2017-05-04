---
title: "在 Office 解决方案中使用本地数据库文件概述 | Microsoft Docs"
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
helpviewer_keywords: 
  - "数据 [Visual Studio 中的 Office 开发], 本地"
  - "本地数据 [Visual Studio 中的 Office 开发]"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 数据"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 在 Office 解决方案中使用本地数据库文件概述
  可以在 Office 解决方案可以包含数据库文件，如 SQL Server express \(.mdf\) 文件或 Microsoft Office Access \(.mdb\) 文件，这些文件。  这样，最终用户不需要维护中央数据库就可以维护本地数据库。例如，在仅用于单台计算机的本地库存解决方案中。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 将数据库文件导入项目  
 若要将数据库文件导入项目，请使用**“数据源配置向导”**来创建基于该数据库文件的数据源。  该向导会将数据库文件和类型化数据集添加到项目中。  
  
## 部署数据库文件  
 **“数据源配置向导”**使用相对路径创建与本地数据库文件的连接。  这样，在保留文件相对位置的情况下，可以将解决方案从一台计算机复制到另一台计算机上。  
  
 如果要将解决方案部署到服务器，然后将文档分发给每个最终用户，则还必须手动分发数据库文件，并将该文件安装在相对于文档的同一位置。  这意味着，最终用户如果不移动数据库文件，就不能将文档移动到自己的计算机中的新位置。  
  
## 本地数据库文件和对数据集进行缓存  
 在 Microsoft Office Excel 和 Microsoft Office Word 的文档级解决方案中，通过使用特性 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 标记数据集实例，可以在文档中缓存数据集。  使用**“数据源配置向导”**将数据库文件添加到项目中时，类型化数据集会自动添加到项目中。  基本上不需要对此数据集应用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>，因为数据已经在用户的计算机上。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：使用宿主控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [缓存数据](../vsto/caching-data.md)  
  
  