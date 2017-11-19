---
title: "如何： 允许代码使用受限权限的文档的后台运行 |Microsoft 文档"
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
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d5ab02ea2eb2d34a82607b8f7fd4fbf3f02dd76
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>如何：允许代码在具有受限制权限的文档的后台运行
  Microsoft Office 的信息权限管理 (IRM) 功能可用于将权限限制到文档或工作簿。 默认情况下，不允许的限制的 Microsoft Office Word 文档或 Microsoft Office Excel 工作簿背后的代码运行。 你可以更改默认值，以便你的托管的代码扩展可以访问的对象模型，并且该解决方案将适用。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您必须是文档或工作簿的作者或完全控制访问权限才能进行更改的权限设置。  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>若要允许代码使用受限权限的文档的后台运行  
  
1.  在 Word 或 Excel 中打开的文档或工作簿。  
  
2.  单击**文件**选项卡上，依次指向**准备**，指向**限制权限**，然后单击**受限访问**。  
  
    > [!NOTE]  
    >  首次使用，将提示您安装 Windows Rights Management 客户端。 安装客户端后，你可能需要重复这些步骤。  
  
3.  在**权限**对话框中，选择**限制此文档的权限**，然后单击**更多选项**。  
  
4.  下**用户的其他权限**，选择**以编程方式访问内容**。  
  
 Word 或 Excel 将允许以编程方式访问的对象模型。  
  
## <a name="see-also"></a>另请参阅  
 [信息权限管理与托管的代码扩展概述](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [在文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文档上的密码保护](../vsto/password-protection-on-office-documents.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [保护 Office 解决方案](../vsto/securing-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  