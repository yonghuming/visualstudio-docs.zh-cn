---
title: "文档在文档级解决方案中的保护 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ceecad94d3f9bb910f47484e5deab0f20876a0d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="document-protection-in-document-level-solutions"></a>文档级解决方案中的文档保护
  你可以使用 Microsoft Office Word 和 Microsoft Office Excel 文档级项目中的保护的功能。 这些功能可以阻止未经授权的用户对受保护的文档部分进行更改。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 使用 Excel，你可以启用保护打开和关闭在设计器中打开工作簿时。 使用 Word，您可以开启保护仅在设计器之外。 在运行时，可以启用或禁用保护，以编程方式为 Word 和 Excel。  
  
 所有控件是在设计器中打开的文档上启用文档保护时，都会从**工具箱**或将变得不可用，您无法将拖动繁**数据源**对文档的窗口。  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument 和受保护的文档  
 当受保护文档时，不能在文档外从访问数据缓存。 不能使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类来检索或处理在受保护的文档中，缓存的数据或使用的其他方法<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>类。  
  
## <a name="word-document-protection-in-the-designer"></a>在设计器中的 Word 文档保护  
 如果在 Visual Studio 中打开时，可添加到 Word 文档或模板保护，无法开始实施设计器中的保护。 文档处于设计模式下，打开在 Visual Studio 中，而它之前，必须在运行模式下你可以开始实施保护。  
  
 但是，如果你创建使用启用了保护的现有 Word 文档的项目，在设计器中打开时保护此文档。 不能编辑受保护的文档，部分，但你仍然可以编写代码在代码编辑器中自动执行文档。 在 Visual Studio 中打开文档时启用保护，也不能生成项目。  
  
 在文档处于设计器中打开，以便你可以编辑该文档并生成项目时，你可以关闭保护。 在进行调试; 时，无法将关闭设计器中的副本的保护在调试期间打开的文档是从一个打开设计器 （输出副本存储在的 \bin\debug 目录，对于 C# 和 Visual Basic 中的 \bin 目录中） 中的单独副本。  
  
 你可以启用通过关闭 Visual Studio 中的项目，打开位于项目目录中，文档的副本并开启保护在设计器中打开的文档的副本保护。  
  
## <a name="enforcing-word-document-protection-on-build"></a>强制在生成的 Word 文档保护  
 Visual Studio 启动强制保护的 Word 文档和模板在生成过程中，以便进行调试打开文档时启用保护。 已使用空密码保护文档。  
  
 保护启用在生成期间因此，如果文档中存在代码<xref:Microsoft.Office.Tools.Word.Document.Startup>可能会导致异常或更改应用程序的行为的事件，此代码可以正确调试。 如果文档打开之后启用保护，则无法调试或测试初始化代码。  
  
## <a name="setting-the-password"></a>设置密码  
 Visual Studio 自动启用保护，但默认情况下提供任何密码。 如果你想文档保护有一个密码，您必须在部署你的解决方案之前添加它。 添加密码，可让授权的用户从文档; 中删除保护如果没有密码，不能轻松地删除保护。 有关设置密码的详细信息，请参阅特定 Office 应用程序中的帮助。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式保护文档和文档的某些部分](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [信息权限管理与托管的代码扩展概述](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office 文档上的密码保护](../vsto/password-protection-on-office-documents.md)   
 [如何： 允许代码使用受限权限的文档的后台运行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  