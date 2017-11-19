---
title: "托管引用 （在 Visual Studio 中的 Office 开发） |Microsoft 文档"
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
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
ms.assetid: 1fa66da0-9d90-4524-ba4f-4da13aab73b5
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2e7bb95ba186c55820ce0c8fd965196ede957b1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managed-reference-office-development-in-visual-studio"></a>托管参考（Visual Studio 中的 Office 开发）
  本部分包含在针对 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Office 项目中使用的命名空间和类型的 API 参考文档。 对于在 Office 项目中使用的针对 .NET Framework 3.5 的有关命名空间和类型的 API 参考文档，请参阅下列 Visual Studio 文档中的参考资料部分： [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)。  
  
> [!NOTE]  
>  开发扩展的 Office 体验跨解决方案是否有兴趣[多个平台](https://dev.office.com/add-in-availability)？ 查看全新[Office 外接程序模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 外接程序具有内存占用较小与 VSTO 外接程序和解决方案，相比，并且你可以通过使用几乎任何 web 编程技术，例如 HTML5、 JavaScript、 CSS3 和 XML 生成它们。  
  
## <a name="in-this-section"></a>本节内容  
 <xref:Microsoft.Office.Tools>  
 包含对 Office 解决方案编程通用的类。 这些类包括 VSTO 加载项的基类、用于在 VSTO 加载项中创建自定义任务窗格的类、用于在 Excel 和 Word 解决方案中创建智能标记的类以及用于在文档级自定义项中创建操作窗格的类。  
  
 <xref:Microsoft.Office.Tools.Excel>  
 包含可以在 Excel 解决方案中使用的宿主控件和宿主项。  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 包含可以在 Excel 解决方案中使用的 Excel 控件和 Windows 窗体控件。  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 包含 VSTO 加载项用于 Outlook 的类，包括用于创建自定义窗体区域的类。  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 包含用于以编程方式修改使用功能区设计器创建的功能区自定义项的类。  
  
 <xref:Microsoft.Office.Tools.Word>  
 包含可以在 Word 解决方案中使用的宿主控件和宿主项。  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 包含可以在 Word 解决方案中使用的 Word 控件和 Windows 窗体控件。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 包含 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类和一组相关的缓存数据类。 这些类可以用于在没有安装 Microsoft Office 的计算机上修改文档级自定义项的某些方面。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 包含 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 接口（可实现该接口以便为 Office 解决方案创建 *部署后操作* ）、可能会在安装 Office 解决方案时引发的异常以及其他属于 Visual Studio 基础结构一部分的 API。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 包含可以由 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]引发的大多数异常、可以用于在文档级自定义项中缓存数据的多个类以及其他属于 Visual Studio 基础结构一部分的 API。  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 包含用于生成 Office 项目的 MSBuild 任务类。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [入门 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  