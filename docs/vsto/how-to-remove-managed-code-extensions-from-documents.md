---
title: "如何：移除文档中的托管代码扩展"
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
  - "托管代码扩展 [Visual Studio 中的 Office 开发], 移除"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：移除文档中的托管代码扩展
  可以通过编程方式从属于 Microsoft Office Word 或 Microsoft Office Excel 文档级自定义项的文档或工作簿中移除自定义项程序集。  用户随后可以打开文档并查看其内容，但是您添加到文档中的任何自定义用户界面 \(UI\) 都不会出现，而且您的代码将不会运行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 可以使用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]提供的某个 RemoveCustomization 方法来移除自定义项程序集。  使用哪个方法取决于您是要在运行时（也就是说，通过在 Word 文档或 Excel 工作簿打开时运行自定义项中的代码）移除自定义项，还是要从关闭的文档或未安装 Microsoft Office 的服务器上的文档中移除自定义项。  
  
 ![链接到视频](../vsto/media/playvideo.png "链接到视频") 如需相关视频演示，请参见 [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782)（如何实现：在 Word 文档中附加或分离 VSTO 程序集）。  
  
### 在运行时移除自定义项程序集  
  
1.  在自定义代码中，调用 <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> 方法（适用于 Word）或 <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> 方法（适用于 Excel）。  此方法只应在不再需要自定义项之后调用。  
  
     在代码中调用此方法的时机取决于使用自定义项的方式。  例如，如果客户直到他们准备好将文档发送到仅文档本身（非自定义项）需要的其他客户端时，才使用您的自定义项功能，则您可以在客户单击它时提供一些调用 RemoveCustomization 的 UI。  或者，如果客户在第一次打开文档时使用数据填充该文档，但自定义项不提供客户直接访问的任何其他功能，则您可以在自定义项完成对文档的初始化后立即调用 RemoveCustomization。  
  
### 从关闭的文档或服务器上的文档中移除自定义项程序集  
  
1.  在不需要 Microsoft Office，如控制台应用程序或 Windows 窗体项目的项目中，添加对 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 程序集。  
  
2.  将以下 **Imports** 或 **using** 语句添加到代码文件顶部。  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  调用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类的静态 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法，并在参数中指定解决方案文档路径。  
  
     下面的代码示例假定您要从桌面上一个名为 **WordDocument1.docx** 的文档中移除自定义项。  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  生成项目并在要移除自定义项的计算机上运行该应用程序。  计算机必须具有 for Office runtime 的 Visual Studio 2010 工具安装的。  
  
## 请参阅  
 [使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何：将托管代码扩展附加到文档](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  