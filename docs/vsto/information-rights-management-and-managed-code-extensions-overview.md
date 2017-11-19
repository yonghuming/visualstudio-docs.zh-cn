---
title: "信息权限管理与托管的代码扩展概述 |Microsoft 文档"
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
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ff6c79d6bed7ec1b5a459f64c0e57c8c35ab4e1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>信息权限管理与托管代码扩展概述
  Microsoft Office Word 和 Microsoft Office Excel 提供了信息权限管理 (IRM) 功能，可帮助你防止未经授权的人员查看或更改敏感信息。 有关信息权限管理的工作原理的详细信息，请参阅特定 Office 应用程序中的帮助。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>使用受限权限运行的文档的后台代码  
 如果你的解决方案包含文档或工作簿的使用 IRM，默认情况下，Word 和 Excel 不允许运行任何代码。 如果您是文档作者，或具有完全控制访问权限，你可以更改默认值，以便你解决方案的工作方式。 有关详细信息，请参阅[如何： 向运行后面文档具有受限权限允许代码](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
 IRM 禁止使用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>检索或操作缓存到文档中的数据。  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>最终用户限制到使用托管的代码扩展的文档的权限  
 你的解决方案中具有完全控制访问权限的文档或工作簿的任何人可以使用 IRM 限制权限。 例如，如果一个会计部门在最终用户将使用自动填充数据库中的数据的工作表的解决方案，该用户可能想要允许仅向他或她部门中的人员的更改访问权限和对其他人读取访问权限。 当用户将添加受限的权限时，默认情况下，工作表的代码不能运行，并不将使用数据填充工作表。  
  
 若要解决此问题，具有完全控制访问权限的文档或工作簿的用户必须更改默认权限设置，以允许以编程方式访问的对象模型。 有关详细信息，请参阅[如何： 向运行后面文档具有受限权限允许代码](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文档上的密码保护](../vsto/password-protection-on-office-documents.md)   
 [保护 Office 解决方案](../vsto/securing-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  