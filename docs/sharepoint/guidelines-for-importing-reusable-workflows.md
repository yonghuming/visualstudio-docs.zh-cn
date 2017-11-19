---
title: "导入可重用工作流的准则 |Microsoft 文档"
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
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32e0180f804a8b35946a4d7a4d02f72dd6deb7d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Guidelines for Importing Reusable Workflows
  若要导入在 SharePoint Designer 中创建的可重用工作流，请使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的“导入可重用 SharePoint 2010 工作流”项目模板。 此模板导入*声明性**工作流*([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-仅) 并将其插入转换*代码工作流*，这是你可以使用增强的工作流[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]或[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]代码。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][演练： 将 SharePoint Designer 可重用工作流导入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。  
  
 但“导入可重用 SharePoint 2010 工作流”模板只能导入场解决方案。 若要将工作流部署为沙盒解决方案，请使用“导入 SharePoint 2010 解决方案包”模板将其导入。 但是，如果这样做，则无法将工作流转换为代码工作流，同样也不能对其进行修改。  
  
## <a name="importing-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>使用导入可重用工作流模板中导入可重用工作流  
 如果使用“导入可重用 SharePoint 2010 工作流”模板导入可重用工作流，则可以像运行或更改任何其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 解决方案一样来运行或更改此解决方案，只不过您可能必须手动修复某些项。  
  
### <a name="importing-task-forms"></a>导入任务窗体  
 “导入可重用 SharePoint 2010 工作流”项目模板将导入所有启动窗体和关联窗体，但仅导入一个任务窗体，因为代码工作流架构只允许一个任务窗体。 原始工作流解决方案中的任何其他任务窗体放入**其他已导入文件**文件夹中的**解决方案资源管理器**。  
  
## <a name="importing-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>使用“导入 SharePoint 2010 解决方案包”模板导入可重用工作流  
 如果使用“导入 SharePoint 2010 解决方案包”模板导入可重用工作流，您需要考虑下列问题：  
  
-   在导入工作流后, 可立即部署和运行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]通过选择 F5 键。 但是，如果你更改在导入的解决方案中的工作流中的任何内容，你可能需要手动修复项目中元素，然后才能部署和运行工作流。  
  
-   由于工作流是声明性的不能将代码添加到它。 若要将工作流转换为代码工作流，你必须将其导入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用导入可重用 SharePoint 2010 工作流模板。  
  
-   虽然您可以编辑设计视图中的工作流设计器 (.xoml) 文件，建议你在源视图中编辑它由于工作流设计器显示 false 错误。  
  
-   调试工作流中并不适用于声明性内容。 在中设置断点[!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)]而不会命中。  
  
## <a name="importing-globally-reusable-workflow-solutions"></a>导入全局可重用工作流解决方案  
 无法使用“导入可重用 SharePoint 2010 工作流”模板导入全局可重用工作流。 若要导入全局可重用工作流，您必须将其转换为非全局可重用工作流或必须使用“导入 SharePoint 2010 解决方案包”模板。  
  
 若要将工作流的转换，请一份全局可重用工作流在 SharePoint Designer (通过打开工作流的快捷菜单，然后选择**另存为副本**)。 然后使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的“导入可重用 SharePoint 2010 工作流”模板导入新的可重用工作流。  
  
 若要导入全局可重用工作流而不进行修改，请使用“导入 SharePoint 2010 解决方案包”模板。 如果你使用此方法，此工作流不会转换为代码工作流，而仍为声明性工作流。  
  
## <a name="see-also"></a>另请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [演练：将 SharePoint Designer 可重用工作流导入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  