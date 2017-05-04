---
title: "Office 文档的密码保护 | Microsoft Docs"
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
  - "Office 文档 [Visual Studio 中的 Office 开发, 受限权限"
  - "密码 [Visual Studio 中的 Office 开发], 文档保护"
  - "权限 [Visual Studio 中的 Office 开发]"
  - "工作簿 [Visual Studio 中的 Office 开发], 受限权限"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Office 文档的密码保护
  在 Microsoft Office Word 文档和 Microsoft Office Excel 工作簿上可以设置密码，以使那些不知道密码的人无法打开这些文件。  此选项称为**“打开权限密码”**。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以使用启用了**“打开权限密码”**的现有文档和工作簿来创建文档级项目。  启用了**“打开权限密码”**的 Word 和 Excel 文档在 Visual Studio 中的行为有所不同。  
  
 有关启用**“打开权限密码”**的信息，请参见 Word 或 Excel 中的帮助。  
  
## Excel 和 Word 的行为  
 您每次在 Visual Studio 中打开启用了**“打开权限密码”**的 Excel 工作簿时，Excel 都会提示您输入密码。  当您生成解决方案时，系统将再次提示您输入密码，因为生成期间将打开文档。  
  
 您第一次在 Visual Studio 中打开启用了**“打开权限密码”**的 Word 文档时，Word 会提示您输入密码。  当您成功输入密码后，**“打开权限密码”**将从文档中被移除，以后打开文档将不再需要密码。  如果您希望解决方案中的文档必须有密码才能打开，您必须在最终生成之后且在部署解决方案之前启用**“打开权限密码”**。  
  
## 请参阅  
 [文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)   
 [信息权限管理与托管代码扩展概述](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [如何：允许代码在具有受限制权限的文档的后台运行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  