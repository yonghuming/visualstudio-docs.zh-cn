---
title: "如何：以编程方式保护文档和文档的某些部分 | Microsoft Docs"
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
  - "文档保护"
  - "文档 [Visual Studio 中的 Office 开发]，文档保护"
  - "Word 文档，保护"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：以编程方式保护文档和文档的某些部分
  你可以为 Microsoft Office Word 文档添加保护，以防止用户对文档进行任何编辑操作。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 还可以将文档的特定区域标记为例外，使指定用户只能编辑文档的这些区域。 例如，你可能希望保护整个文档，但某个特定的书签除外。 可选择添加密码，这样一来，除非用户知道此密码，否则无法删除文档保护。  
  
> [!NOTE]  
>  下面的示例未使用密码保护；但是，在添加文档保护时，你可能想考虑使用密码。 有关详细信息，请参阅 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的“文档保护器示例”。  
  
 你也可以使用内容控件来保护文档的各个部分。 有关详细信息，请参阅[如何：使用内容控件保护文档的某些部分](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)。  
  
## 保护属于文档级自定义项的文档  
  
#### 若要保护属于文档级自定义项的文档  
  
1.  调用项目中 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### 从文档保护中排除 Bookmark 控件  
  
1.  使用 <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> 方法保护整个文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  从文档保护中排除 `Bookmark1`。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### 编译代码  
 若要使用这些代码示例，请从项目内的 `ThisDocument` 类中运行这些示例。 这些代码示例假定在出现此代码的文档中有一个名为 `Bookmark1` 的现有 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。  
  
## 使用 VSTO 外接程序保护文档  
  
#### 使用应用程序级 VSTO 外接程序保护文档  
  
1.  调用要保护的 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> 方法。  
  
     下面的代码示例将保护活动文档。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## 请参阅  
 [文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文档的密码保护](../vsto/password-protection-on-office-documents.md)   
 [如何：允许代码在具有受限制权限的文档的后台运行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [如何：向 Word 文档添加书签控件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  