---
title: "工作流中的窗体支持 |Microsoft 文档"
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
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2c63af83c6ca8249e87d60f23043c0639c7fd43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="form-support-in-workflows"></a>工作流中的窗体支持
  可以在工作流中使用四种类型的窗体： 关联、 启动、 任务和修改。 这些窗体类型可以基于一个 ASPX 窗体或的 InfoPath 窗体。 级别支持[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供了用于将特定表单取决于几个因素，以下表中所述。 有关工作流窗体类型的详细信息，请参阅[工作流窗体概述](http://go.microsoft.com/fwlink/?LinkId=185228)MSDN 网站上。  
  
## <a name="xml-refactoring"></a>XML 重构  
 当您添加到将 ASPX 关联或启动窗体[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]工作流项目项[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]自动重构工作流的 Elements.xml 文件中的 XML，需要引用关联或启动窗体保持同步的属性每当更新的窗体名称或部署路径，或删除该窗体。 但是，工作流，例如任务或修改窗体中，使用其他窗体类型时，将不会重构 Elements.xml 文件。  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>在新的 Visual Studio 工作流中的窗体支持  
 下表列出[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中创建的工作流中的 ASPX 或 InfoPath 窗体上的不同的窗体类型的支持[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
|窗体类型|在处理 ASPX 窗体的 Visual Studio 中创建的工作流|在 Visual Studio 中使用创建的 InfoPath 窗体的工作流|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|关联|-An ASPX 关联窗体可以使用添加到工作流**工作流关联窗体**项模板。<br />在添加、 重命名或删除，窗体或其部署路径更改时，工作流-Elements.xml 文件将重构。<br />-有关详细信息，请参阅[演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-没有 InfoPath 关联窗体模板中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-没有之间集成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 设计器。<br />工作流-Elements.xml 文件不要求进行重构。|  
|启动|-An ASPX 启动窗体可以使用添加到工作流**工作流启动窗体**项模板。<br />在添加、 重命名或删除，窗体或其部署路径更改时，工作流-Elements.xml 文件将重构。<br />-有关详细信息，请参阅[演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-没有 InfoPath 关联窗体模板中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-没有之间集成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 设计器。<br />工作流-Elements.xml 文件不要求进行重构。|  
|任务|-无 ASPX 任务窗体模板，可用于[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 你必须创建的应用程序页，并将代码添加到它。<br />工作流-Elements.xml 文件不要求进行重构。<br />-有关详细信息，请参阅[工作流任务窗体 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-没有 InfoPath 任务窗体模板中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-没有之间集成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 设计器。<br />工作流-Elements.xml 文件不要求进行重构。|  
|修改|-无 ASPX 修改窗体模板可用于[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要添加修改窗体，必须创建的应用程序页，并将代码添加到它。<br />工作流-Elements.xml 文件不要求进行重构。 你必须手动编辑它根据需要。<br />-有关详细信息，请参阅[工作流修改窗体 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-没有 InfoPath 修改窗体模板中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-没有之间集成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 设计器。<br />工作流-Elements.xml 文件不要求进行重构。|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>在导入的 SharePoint 可重用工作流中的窗体支持  
 下表列出[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]可导入到的 SharePoint 可重用工作流中的 ASPX 或 InfoPath 窗体上的不同的窗体类型的支持[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
|窗体类型|具有 SharePoint Designer 从导入将 ASPX 窗体的可重用工作流|具有 SharePoint Designer 从导入的 InfoPath 窗体的可重用工作流|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|关联|的工作流的 Elements.xml 文件中引用它窗体。<br />在窗体是重命名或删除，或其部署路径更改时，工作流-Elements.xml 文件将重构。|-窗体是导入，但不是在工作流的 Elements.xml 中引用。<br />工作流-Elements.xml 文件不要求进行重构。|  
|启动|的工作流的 Elements.xml 文件中的工作流被引用窗体。<br />在窗体是重命名或删除，或其部署路径更改时，工作流-Elements.xml 文件将重构。|-窗体是导入，但不是在工作流的 Elements.xml 中引用。<br />工作流-Elements.xml 文件不要求进行重构。 **注意：**规则和属性必须添加和更改的这种情况下工作。|  
|任务|的工作流的 Elements.xml 文件中引用它窗体。<br />工作流-Elements.xml 文件不要求进行重构。|-窗体是导入，但不是在工作流的 Elements.xml 中引用。<br />工作流-Elements.xml 文件不要求进行重构。 **注意：**规则和属性必须添加和更改的这种情况下工作。|  
|修改|不适用。 无法在 SharePoint Designer 创建 ASPX 修改窗体。|不适用。 除内置的 SharePoint 服务器工作流，工作流导出时不包含在.wsp 文件之外，无法在 SharePoint 设计器中，创建 InfoPath 修改窗体。|  
  
## <a name="see-also"></a>另请参阅  
 [演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [从现有 SharePoint 站点导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  