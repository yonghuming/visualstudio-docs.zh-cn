---
title: "按 Office 应用程序和项目类型提供的功能 |Microsoft 文档"
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
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
ms.assetid: 3e9aa4d3-affb-4f76-bc67-49fe5f26a6a1
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13da2a068348478be8511e1c5624059b0d063bac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="features-available-by-office-application-and-project-type"></a>按 Office 应用程序和项目类型提供的功能
  Visual Studio 具有几种类型的项目模板，它们支持 Microsoft Office 应用程序的不同业务方案，包括以下类型：  
  
-   文档级自定义项。  
  
-   VSTO 外接程序  
  
 并非所有应用程序都可以使用所有项目类型。 例如，文档级项目仅可用于 Microsoft Office Word 和 Microsoft Office Excel。 同样，某些功能仅可用于特定类型的项目或应用程序。 例如，操作窗格仅在文档级项目中可用，而功能区扩展仅可用于某些应用程序。 有关不同项目类型的详细信息，请参阅[Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Office 项目模板仅在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的某些版本中可用。 有关详细信息，请参阅 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)。  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>不同 Microsoft Office 应用程序的可用项目类型  
 下表显示了可使用所有项目类型的应用程序。  
  
|项目类型|Microsoft Office 应用程序|  
|-------------------|----------------------------------|  
|文档级自定义项|Excel<br /><br /> Word|  
|VSTO 外接程序|Excel<br /><br /> InfoPath（仅 InfoPath 2013 和 InfoPath 2010）<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> 项目<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>不同项目类型中的可用功能  
 下表显示了提供每项功能的项目类型。  
  
|功能|提供该功能的项目类型|其他阅读材料|  
|-------------|--------------------------------------------|---------------------|  
|操作窗格。|文档级项目。|[操作窗格概述](../vsto/actions-pane-overview.md)|  
|ClickOnce 部署。|VS 与文档级项目。|[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)|  
|自定义任务窗格。|以下应用程序的 VSTO 外接程序项目：<br /><br /> Excel<br />-InfoPath （InfoPath 2013 和 InfoPath 2010 仅）<br />-Outlook<br />-PowerPoint<br />单词|[自定义任务窗格](../vsto/custom-task-panes.md)|  
|自定义 XML 部件。|文档级项目。<br /><br /> 以下应用程序的应用程序级项目：<br /><br /> Excel<br />-PowerPoint<br />单词|[自定义 XML 部件概述](../vsto/custom-xml-parts-overview.md)|  
|数据缓存。|文档级项目。|[文档级自定义项中的缓存数据](../vsto/cached-data-in-document-level-customizations.md)|  
|向其他 Microsoft Office 解决方案公开 VSTO 外接程序中的对象。|VSTO 外接程序项目。|[从其他 Office 解决方案调用 VSTO 外接程序中的代码](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|以下主机控件：<br /><br /> -图表<br />-ListObject<br />-NamedRange<br />的内容控件<br />书签|文档级项目。<br /><br /> 用于 Word 和 Excel 的 VSTO 外接程序项目。|[主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)|  
|以下主机控件：<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|文档级项目。|[主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)|  
|多项目部署。|文档级项目。<br /><br /> VSTO 外接程序项目。|[演练： 部署在单个的 ClickOnce 安装程序的多个 Office 解决方案](http://msdn.microsoft.com/en-us/051223c0-4082-4799-b78b-a4763a9def55)|  
|Outlook 窗体区域。|用于 Outlook 的 VSTO 外接程序项目。|[创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)|  
|部署后操作。|文档级项目。<br /><br /> VSTO 外接程序项目。|[演练： 在 ClickOnce 安装后将文档复制到最终用户计算机](http://msdn.microsoft.com/en-us/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|功能区自定义。|文档级项目。<br /><br /> 以下应用程序的 VSTO 外接程序项目：<br /><br /> Excel<br />-InfoPath （InfoPath 2013 和 InfoPath 2010 仅）<br />-Outlook<br />-PowerPoint<br />项目<br />Visio<br />单词|[功能区概述](../vsto/ribbon-overview.md)|  
|可视化文档设计器。|文档级项目。|[Visual Studio 环境中的 Office 项目](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>另请参阅  
 [入门 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [功能区概述](../vsto/ribbon-overview.md)   
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [文档级自定义项中缓存的数据](../vsto/cached-data-in-document-level-customizations.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  