---
title: "如何：将托管代码扩展附加到文档"
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
  - "文档 [Visual Studio 中的 Office 开发], 托管代码扩展"
  - "托管代码扩展 [Visual Studio 中的 Office 开发], 附加"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 如何：将托管代码扩展附加到文档
  您可以将自定义项程序集附加到现有的 Microsoft Office Word 文档或 Microsoft Office Excel 工作簿中。  该文档或工作簿可以在 Microsoft Office 项目和开发工具支持在 Visual Studio 的所有文件格式。  有关更多信息，请参见[文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 若要将自定义项附加到 Word 或 Excel 文档，请使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。  由于将 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类设计为在未安装 Microsoft Office 的计算机上运行，因此，您可以在与 Microsoft Office 开发工具（如控制台或 Windows 窗体应用程序）无直接关系的解决方案中使用此方法。  
  
> [!NOTE]  
>  如果代码需要指定文档所没有的控件，自定义项将加载失败。  
  
 ![链接到视频](../vsto/media/playvideo.png "链接到视频") 如需相关视频演示，请参见 [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782)（如何实现：在 Word 文档中附加或分离 VSTO 程序集）。  
  
### 将托管代码扩展附加到文档  
  
1.  在不需要 Microsoft Office，如控制台应用程序或 Windows 窗体项目的项目中，添加对 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 和 Microsoft.VisualStudio.Tools.Applications.Runtime.dll 程序集。  
  
2.  将以下 **Imports** 或 **using** 语句添加到代码文件顶部。  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  调用静态 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。  
  
     下面的代码示例使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 重载。  此重载采用文档的完整路径和一个 <xref:System.Uri>，后者指定要附加到文档的自定义项的部署清单的位置。  此示例假定名为 **WordDocument1.docx** 的 Word 文档位于桌面上，并且部署清单位于一个名为 **Publish** 的文件夹中，该文件夹也位于桌面上。  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  生成项目并在要附加自定义项的计算机上运行该应用程序。  计算机必须具有 for Office runtime 的 Visual Studio 2010 工具安装的。  
  
## 请参阅  
 [使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何：移除文档中的托管代码扩展](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office 解决方案中的应用程序和部署清单](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  