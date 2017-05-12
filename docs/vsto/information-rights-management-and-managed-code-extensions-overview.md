---
title: "信息权限管理与托管代码扩展概述"
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
  - "文档 [Visual Studio 中的 Office 开发], 受限权限"
  - "信息权限管理 [Visual Studio 中的 Office 开发]"
  - "IRM [Visual Studio 中的 Office 开发]"
  - "Office 文档 [Visual Studio 中的 Office 开发, 受限权限"
  - "权限管理 [Visual Studio 中的 Office 开发]"
  - "工作簿 [Visual Studio 中的 Office 开发], 受限权限"
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 信息权限管理与托管代码扩展概述
  Microsoft Office Word 和 Microsoft Office Excel 提供了一项“信息权限管理”\(IRM\) 功能，此功能可以帮助防止未经授权的人员查看或更改敏感信息。  有关“信息权限管理”如何工作的详细信息，请参见特定 Office 应用程序中的“帮助”。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 在具有受限制权限的文档的后台运行代码  
 如果您的解决方案包含使用 IRM 的文档或工作簿，Word 或 Excel 默认将不允许任何代码运行。  如果您是文档的作者或者您具有“完全控制”访问权限，您可以更改默认设置以使解决方案能够工作。  有关更多信息，请参见[如何：允许代码在具有受限制权限的文档的后台运行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
 IRM 阻止使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> 来检索或操作缓存在文档中的数据。  
  
## 使用托管代码扩展的文档的最终用户限制权限  
 对您的解决方案中的文档或工作簿具有“完全控制”访问权限的任何用户都能够使用“信息权限管理”限制权限。  例如，如果财务部门的某个最终用户使用一个自动将数据库中的数据填充到工作表的解决方案，该用户可能希望只授予本部门用户“更改”访问权限，而授予其他部门的用户“读”访问权限。  默认情况下，当此用户添加受限制的权限时，工作表后台的代码不运行，因此不会将数据填充到该工作表。  
  
 要解决此问题，必须由某位对于该文档或工作簿具有“完全控制”访问权限的用户对默认权限设置进行更改，以允许通过编程的方式访问该对象模型。  有关更多信息，请参见[如何：允许代码在具有受限制权限的文档的后台运行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
## 请参阅  
 [文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文档的密码保护](../vsto/password-protection-on-office-documents.md)   
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  