---
title: "文档宿主项"
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
  - "文档 [Visual Studio 中的 Office 开发]"
  - "文档 [Visual Studio 中的 Office 开发]，文档宿主项"
  - "文档宿主项"
  - "Word [Visual Studio 中的 Office 开发]，Word 文档"
  - "Word [Visual Studio 中的 Office 开发]"
  - "Word 文档"
  - "宿主项 [Visual Studio 中的 Office 开发]，文档"
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 文档宿主项
  <xref:Microsoft.Office.Tools.Word.Document> 宿主项这种类型从 Word 的主互操作程序集扩展类型 <xref:Microsoft.Office.Interop.Word.Document>。<xref:Microsoft.Office.Tools.Word.Document> 宿主项提供与 <xref:Microsoft.Office.Interop.Word.Document> 对象完全相同的属性、方法和事件，但它还公开其他事件并充当宿主控件和 Windows 窗体控件的容器。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 在文档级项目中，有代表你的项目中的文档的默认 <xref:Microsoft.Office.Tools.Word.Document> 宿主项。 在 VSTO 外接程序项目中，可以在运行时生成 <xref:Microsoft.Office.Tools.Word.Document> 主机项。  
  
## 了解文档级项目中的文档宿主项  
 若要访问你的项目中的文档，请使用 `ThisDocument` 类。 当你创建文档级项目时，Visual Studio 将生成 `ThisDocument` 类来充当 Word 和自定义代码之间的通信链接。 利用 `ThisDocument` 类，你可以访问 <xref:Microsoft.Office.Tools.Word.Document> 宿主项的成员，以在自定义项中执行基本任务，例如当文档打开或关闭时运行代码。 也可以使用该类将控件添加到文档。 通过组合不同的控件集并编写代码，可将控件绑定到数据、从用户处收集信息并响应用户操作。 有关详细信息，请参阅[对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)。  
  
 `ThisDocument` 类提供了一个位置，你可以在该位置开始编写项目中的代码。 因为该类提供与 Word 主互操作程序集中的 <xref:Microsoft.Office.Interop.Word.Document> 对象完全相同的属性、方法和事件，所以也可以使用 `ThisDocument` 访问 Word 的对象模型。 有关详细信息，请参阅[Word 对象模型概述](../vsto/word-object-model-overview.md)。  
  
### 文档级项目中的文档宿主项的限制  
 文档级项目只能包含一个 <xref:Microsoft.Office.Tools.Word.Document> 宿主项（即 `ThisDocument` 类）。 不能在设计时将新的 <xref:Microsoft.Office.Tools.Word.Document> 宿主项添加到项目，也不能在运行时从文档级自定义项创建新的 <xref:Microsoft.Office.Tools.Word.Document> 宿主项。  
  
 如果在运行时创建新的 Word 文档，则该文档为类型 <xref:Microsoft.Office.Interop.Word.Document>。 因为它不是宿主项，所以它不能包含任何宿主控件或 Windows 窗体控件。 有关在运行时创建文档的详细信息，请参阅 [如何：以编程方式新建文档](../vsto/how-to-programmatically-create-new-documents.md)。  
  
## 了解应用程序级项目中的文档宿主项  
 在 VSTO 外接程序项目中，可以在运行时为 Word 中打开的任何文档生成 <xref:Microsoft.Office.Tools.Word.Document> 宿主项。 可以使用 <xref:Microsoft.Office.Tools.Word.Document> 宿主项将控件添加到关联的文档中，或处理 <xref:Microsoft.Office.Interop.Word.Document> 对象中不可用的事件。  
  
 若要生成 <xref:Microsoft.Office.Tools.Word.Document> 宿主项，请使用 GetVstoObject 方法。 有关详细信息，请参阅[在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## 请参阅  
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  