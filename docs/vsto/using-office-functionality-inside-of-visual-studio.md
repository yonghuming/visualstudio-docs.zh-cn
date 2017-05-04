---
title: "在 Visual Studio 内使用 Office 功能 | Microsoft Docs"
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
  - "Office 应用程序 [Visual Studio 中的 Office 开发]"
  - "Visual Studio 内的 Office 功能"
  - "安全性 [Visual Studio 中的 Office 开发], 文档保护"
ms.assetid: 593fd583-57e5-4ed5-8489-89f73b886c6c
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 在 Visual Studio 内使用 Office 功能
  创建文档级项目时，文档和关联的应用程序承载于 Visual Studio 内，因此可以直接设计和使用文档。  在 Visual Studio 中打开 Microsoft Office 应用程序时，该应用程序通常按预期方式工作。  但是，应用程序的某些功能将有所不同或不可用。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 文档保护  
 Microsoft Office Word 和 Microsoft Office Excel 提供可在项目中使用的文档保护功能。  但是，如果在 Visual Studio 中打开文档时启用了文档保护，则此功能可以阻止您进行某些设计更改。  有关更多信息，请参见[文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)。  
  
## 信息权限管理  
 Microsoft Office Word 和 Microsoft Office Excel 中提供信息权限管理 \(IRM\) 功能。  IRM 可以帮助您防止未经授权的人员查看或更改敏感信息。  但是，IRM 也可以阻止代码运行。  有关更多信息，请参见[信息权限管理与托管代码扩展概述](../vsto/information-rights-management-and-managed-code-extensions-overview.md)。  
  
## 密码保护  
 可以对 Microsoft Office Word 文档和 Microsoft Office Excel 工作簿设置密码，以使那些不知道密码的人无法打开这些文件。  密码保护在 Word 与 Excel 中的实施方式不同，并且可能会影响您的开发过程。  有关更多信息，请参见[Office 文档的密码保护](../vsto/password-protection-on-office-documents.md)。  
  
## 请参阅  
 [文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)   
 [信息权限管理与托管代码扩展概述](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office 文档的密码保护](../vsto/password-protection-on-office-documents.md)   
 [如何：打开 Office 解决方案但不运行代码](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  