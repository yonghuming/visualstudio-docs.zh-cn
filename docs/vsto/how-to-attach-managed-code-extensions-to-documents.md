---
title: "如何： 将托管的代码扩展附加到文档 |Microsoft 文档"
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
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3f5703b54a1deb96e9d6719c2726164e1002a18f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>如何：将托管代码扩展附加到文档
  可以将自定义程序集附加到一个现有的 Microsoft Office Word 文档或 Microsoft Office Excel 工作簿。 Microsoft Office 项目和 Visual Studio 中的开发工具都支持的任何文件格式可以是文档或工作簿。 有关详细信息，请参阅[体系结构的文档级自定义](../vsto/architecture-of-document-level-customizations.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 若要将自定义项附加到 Word 或 Excel 的文档，使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类。 因为<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类旨在没有安装 Microsoft Office 的计算机上运行，则可以在与 Microsoft Office 开发 （如控制台或 Windows 窗体应用程序） 不直接相关的解决方案中使用此方法。  
  
> [!NOTE]  
>  自定义项将无法加载如果代码需要指定的文档没有的控件。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[i： 不要如何附加或分离 VSTO 程序集从 Word 文档？](http://go.microsoft.com/fwlink/?LinkId=136782)。  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>将托管的代码扩展附加到文档  
  
1.  在项目中，不需要 Microsoft Office，如控制台应用程序或 Windows 窗体项目，添加对 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 和 Microsoft.VisualStudio.Tools.Applications.Runtime.dll 的引用程序集。  
  
2.  添加以下**导入**或**使用**到你的代码文件顶部的语句。  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  调用静态<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法。  
  
     下面的代码示例使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>重载。 此重载采用文档的完整路径和<xref:System.Uri>，指定你想要附加到文档的自定义项的部署清单的位置。 此示例假定 Word 文档名为**WordDocument1.docx**是在桌面上，和部署清单位于名为的文件夹**发布**这也是在桌面上。  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  生成项目并想要附加自定义项的计算机上运行应用程序。 计算机必须具有 Visual Studio 2010 Tools for Office Runtime 安装。  
  
## <a name="see-also"></a>另请参阅  
 [使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何： 从文档中删除托管的代码扩展](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office 解决方案中的应用程序和部署清单](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  