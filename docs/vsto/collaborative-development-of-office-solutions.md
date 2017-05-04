---
title: "合作开发 Office 解决方案 | Microsoft Docs"
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
  - "协作开发 [Visual Studio 中的 Office 开发]"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 协作开发"
  - "Visual Studio 中的 Office 开发, 协作"
  - "源控件 [Visual Studio 中的 Office 开发]"
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 合作开发 Office 解决方案
  多个开发人员可以共同开发 Office 项目，方法与他们合作开发其他 Visual Studio 项目的方法相同。  Visual Studio 可在每台计算机上正确地定位 Microsoft Office 安装，即使 Office 安装在不同的位置中。  但是，您必须了解一些重要的注意事项。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 调试属性不共享  
 在源代码管理下，调试属性不在多个用户间共享。  Visual Basic 和 Visual C\# 项目将调试属性存储在特定于用户的文件（*项目名*.vbproj.user 或 *项目名*.csproj.user）中，并且此文件不受源代码管理。  如果有多人正在调试，则每个人都必须手动输入调试属性。  
  
 如果项目驻留在网络共享上而不是在源代码管理中，则必须采取一些额外的步骤，以允许合作开发人员打开解决方案和测试程序集。  
  
## 源代码管理需要签出所有文件  
 如果对您的项目进行源代码管理，您应当在每次更改代码文件时签出**“解决方案资源管理器”**中代码文件下的所有文件（比如 ThisDocument、ThisWorkbook 或 ThisAddIn 代码文件），即使这些文件默认情况下处于隐藏状态。  如果只签出顶层的代码文件，您的更改可能会丢失。  
  
 进行更改之后，请将所有文件重新签回。  有关项目中隐藏的代码文件的更多信息，请参见 [Visual Studio 环境中的 Office 项目](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## 网络上的信息协作的安全性  
 对于位于网络位置（比如 \\\\*服务器名*\\*共享名*）的所有文档级解决方案，必须将完全限定位置添加到您所使用的 Microsoft Office 应用程序中的受信任文件夹列表。  选择选项以在包括主文件夹下的子目录，或者专门将调试和生成文件夹添加到受信任文件夹列表。  有关如何执行该操作的更多信息，请参见 [向文档授予信任](../vsto/granting-trust-to-documents.md)。  
  
 在生成时自动创建的临时证书不受密码保护。  这些证书包含开发人员的登录名和其他个人信息。  如果部署用临时证书签名的自定义项，其他人将能够访问此信息。  
  
## 请参阅  
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)  
  
  