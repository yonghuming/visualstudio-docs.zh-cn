---
title: "如何：打开 Office 解决方案但不运行代码 | Microsoft Docs"
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
  - "程序集 [Visual Studio 中的 Office 开发], 跳过"
  - "跳过程序集"
  - "文档 [Visual Studio 中的 Office 开发], 不运行代码即可打开"
  - "Office 文档 [Visual Studio 中的 Office 开发, 不运行代码即可打开"
  - "Office 解决方案 [Visual Studio 中的 Office 开发], 打开"
  - "打开 Office 解决方案"
  - "解决方案 [Visual Studio 中的 Office 开发], 打开"
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：打开 Office 解决方案但不运行代码
  即使最终用户的 Office 应用程序中的“安全性”设置已设为“高”，使用托管代码扩展创建的 Microsoft Office 解决方案仍然可以运行。  这是因为 .NET 程序集代码安全性由 Microsoft .NET Framework 管理，而不是由 Microsoft Office 管理。  
  
 但是，有时您可能需要打开文档而不运行代码。  例如，在打开文档时运行的代码可能会改动内容，但是您想要在代码更改文档之前更新文档的外观。  或者您可能想要将包含特定信息的文档发送给某人，但不想运行代码，也不希望代码有可能改动内容。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有多种方式可以在不运行程序集代码的情况下打开包含托管代码扩展的文档或工作簿。  
  
### 通过使用 Shift 键来跳过程序集  
  
-   在按下 Shift 键的同时从**“文件”**菜单上打开文档和工作簿，可以阻止 Word 和 Excel 在打开文档时引发初始化事件。  
  
    > [!NOTE]  
    >  如果从**“开始”**任务窗格中打开文档或工作簿，按下 Shift 不会跳过代码。  此外，在文档打开以后，按下 Shift 不会阻止引发事件。  
  
     如果要打开文档以便修改，但又不先运行代码和改动内容，这种方式将是有用的。  
  
### 通过重命名或移除程序集来跳过程序集  
  
-   如果您在程序集所在的计算机上拥有必要的权限，则可以重命名或移除该程序集，以使文档或工作簿无法找到它。  这样会导致在每次当开 Office 文档时引发一个错误。  
  
     如果该解决方案由多人使用，这种方法将阻止所有人运行该解决方案。  如果在代码或引用的服务器中发现问题，并且您想要阻止所有用户执行它，那么这种方法可能是有用的。  
  
## 请参阅  
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [Office 解决方案中的应用程序和部署清单](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  