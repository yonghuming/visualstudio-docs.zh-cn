---
title: "如何： 打开 Office 解决方案但不运行代码 |Microsoft 文档"
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
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74cc162e0323656bea9d48c8458eaf77519fdc14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-office-solutions-without-running-code"></a>如何：打开 Office 解决方案但不运行代码
  创建具有托管的代码扩展的 Microsoft Office 解决方案运行，即使在最终用户的 Office 应用程序中的安全设置设为高。 这是因为.NET 程序集代码安全管理的 Microsoft.NET Framework 中，不是由 Microsoft Office。  
  
 但是，是的时候你可能想要不运行代码即可打开的文档。 例如，当文档打开时运行的代码可能会更改此内容，但你想要更新文档之前，会查找代码更改它的方式。 或你可能想要在其中具有一些信息将文档发送到人，并不希望代码来运行，并可能更改此内容。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有多种方法打开的文档或工作簿，而无需运行的程序集代码中包含托管的代码扩展。  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>若要通过使用 SHIFT 键绕过该程序集  
  
-   打开文档和工作簿从**文件**菜单时按住 SHIFT 键，以防止 Word 和 Excel 打开文档时引发初始化事件。  
  
    > [!NOTE]  
    >  如果你打开文档或工作簿从**入门**任务窗格中，按住 shift 键不跳过代码。 此外，按住 shift 键不会阻止事件打开文档后引发。  
  
     此方法很有用，如果你想要打开的文档的代码运行和第一次更改文档无需进行更改。  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>若要通过重命名或移除它绕过程序集  
  
-   如果程序集所在的计算机上具有必要的权限，可以重命名或删除程序集，以便文档或工作簿找不到它。 这会导致每次打开该 Office 文档时引发错误。  
  
     如果解决方案由多人使用，此方法将运行状态，为所有这些阻止解决方案。 如果在代码或引用的服务器中发现有问题，并且你想要停止从执行它的所有用户，这会很有用。  
  
## <a name="see-also"></a>另请参阅  
 [保护 Office 解决方案](../vsto/securing-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [Office 解决方案中的应用程序和部署清单](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  