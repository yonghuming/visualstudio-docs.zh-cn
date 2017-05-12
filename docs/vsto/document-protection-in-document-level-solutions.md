---
title: "文档级解决方案中的文档保护"
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
  - "Office 文档 [Visual Studio 中的 Office 开发], 受限权限"
  - "权限 [Visual Studio 中的 Office 开发]"
  - "受限权限 [Visual Studio 中的 Office 开发]"
  - "工作簿 [Visual Studio 中的 Office 开发], 受限权限"
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 文档级解决方案中的文档保护
  您可以在文档级项目中使用 Microsoft Office Word 和 Microsoft Office Excel 的保护功能。  这些功能可以阻止未经授权的用户更改文档中受保护的部分。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 使用 Excel，您可以在工作簿在设计器中处于打开状态时打开或关闭保护功能。  使用 Word，您只能在设计器外部打开保护功能。  运行时，对于 Word 和 Excel，您都可以通过编程方式启用或禁用保护功能。  
  
 对设计器中打开的文档启用了文档保护功能后，所有控件都将从**“工具箱”**中移除或变得不可用，您无法将任何对象从**“数据源”**窗口拖动到文档中。  
  
## ServerDocument 和受保护的文档  
 如果文档受保护，则无法从文档外部访问数据缓存。  您不能使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类检索或处理受保护文档中缓存的数据，也不能使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> 类的其他方法。  
  
## 设计器中的 Word 文档保护  
 如果您在 Word 文档或模板在 Visual Studio 中处于打开状态时对其添加保护，则无法在设计器中开始强制保护。  文档在 Visual Studio 中处于打开状态时为设计模式，它必须为运行模式，您才能开始强制保护。  
  
 不过，如果您创建的项目使用启用了保护的现有 Word 文档，则在设计器中打开该文档时，它是受保护的。  您无法编辑文档中受保护的部分，但仍可以在代码编辑器中编写代码以自动执行文档。  如果文档在 Visual Studio 中处于打开状态时启用了保护，则您也无法生成项目。  
  
 您可以在文档在设计器中处于打开状态时关闭保护功能，以便可以编辑文档并生成项目。  当您正在调试时，不能关闭设计器中副本的保护功能；调试时打开的文档不同于设计器中打开的副本（在 Visual Basic 中，输出副本存储在 \\bin 目录中，在 C\# 中存储在 \\bin\\debug 目录中）。  
  
 您可以通过在 Visual Studio 中关闭项目，打开项目目录中文档的副本，然后打开保护，对在设计器中打开的文档副本启用保护功能。  
  
## 在生成时强制 Word 文档保护  
 生成过程中，Visual Studio 会对 Word 文档和模板启动强制保护，以便在文档打开以进行调试时启用保护。  文档由一个空密码保护。  
  
 生成时将启用保护功能，以便当文档的 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件中存在可能导致异常或更改应用程序行为的代码时，可以正确调试此代码。  如果在文档已打开后启用保护功能，可能无法调试或测试初始化代码。  
  
## 设置密码  
 Visual Studio 会自动启用保护，但默认情况下不提供密码。  如果您希望文档保护有密码，必须在部署解决方案之前添加密码。  通过添加密码，您将能够允许经过授权的用户移除文档的保护；如果没有密码，就不太容易移除保护。  有关设置密码的详细信息，请参见特定 Office 应用程序中的帮助。  
  
## 请参阅  
 [如何：以编程方式保护文档和文档的某些部分](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [信息权限管理与托管代码扩展概述](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office 文档的密码保护](../vsto/password-protection-on-office-documents.md)   
 [如何：允许代码在具有受限制权限的文档的后台运行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  