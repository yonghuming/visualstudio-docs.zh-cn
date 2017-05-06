---
title: "Bookmark 控件"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Toolbox.Bookmark"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "书签，控制"
  - "Bookmark 控件，数据绑定"
  - "Bookmark 控件，事件"
  - "Bookmark 控件"
ms.assetid: 940bf165-18c9-4db8-a46c-aad786b8bbad
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Bookmark 控件
  <xref:Microsoft.Office.Tools.Word.Bookmark> 控件是一个具有唯一名称且用于公开事件的书签，可以绑定到数据。 可以将书签用作占位符以在 Microsoft Office Word 文档中标记项或位置。<xref:Microsoft.Office.Tools.Word.Bookmark> 控件是 <xref:Microsoft.Office.Interop.Word.Bookmark> 对象和 <xref:Microsoft.Office.Interop.Word.Range> 对象的组合。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 在文档级项目中，你可以在设计时或运行时向文档中添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 在 VSTO 外接程序项目中，可以在运行时向任何打开的文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 有关更多信息，请参见[如何：向 Word 文档添加书签控件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。  
  
## 将数据绑定到控件  
 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件支持简单数据绑定。 应该使用 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 属性将书签绑定到数据源。 书签的默认数据绑定属性是 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 属性。  
  
 如果更新绑定数据集内的数据，则 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件会反映所做的更改。  
  
 在文档级项目中，还可以使用“数据源”窗口将数据绑定到书签。 有关详细信息，请参阅[如何：用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)。  
  
## 格式化  
 可应用于 <xref:Microsoft.Office.Interop.Word.Bookmark> 的格式设置也可应用于 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 其中包括字体、缩进、间距、编号和样式。  
  
## 向书签分配文本  
 <xref:Microsoft.Office.Interop.Word.Bookmark> 对象和 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件之间的另一个差异在于将文本分配给书签时其行为方式的不同。 如果向零长度 <xref:Microsoft.Office.Interop.Word.Bookmark> 分配文本，文本将被追加到书签右侧，且书签的长度保持为零。 但是，如果向零长度 <xref:Microsoft.Office.Tools.Word.Bookmark> 分配文本，文本将被插入到书签中，且书签的长度将扩展到所插入字符的总数。  
  
 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件还具有 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 属性。 此属性与 <xref:Microsoft.Office.Tools.Word.Bookmark> 的 <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> 属性或 <xref:Microsoft.Office.Interop.Word.Bookmark> 对象的 <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> 属性上可用的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 属性不同。  
  
|Text 属性|描述|  
|-------------|--------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|使用此属性可以在书签内显示文本，并使书签保留在文档中。 向书签分配文本会扩展书签范围，但不会删除书签。<br /><br /> 例如，`Bookmark1.Text = "Hello world"` 将文本插入书签中，且使书签保持原样。|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|使用此属性可在书签位置处显示文本，并自动删除该书签。 例如，`Bookmark1.Range.Text = "Hello world"` 将文本插入书签中，并删除该书签。|  
  
## 在设计时重命名控件  
 在文档级项目中，将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件从“工具箱”拖到文档中时，Visual Studio 会自动为该控件生成一个名称。 可以在“属性”窗口中更改控件的名称。  
  
## 重叠控件  
 书签控件可以相互重叠；也就是说，多个书签可以共享相同文本。 向其中一个重叠书签分配新文本时，该书签将仅包含新文本，并且书签之间将不再重叠。 此时，另一个书签将仅包含未在原来的重叠书签之间共享的文本。  
  
 下表说明句子“This is sample text.” 如何由两个重叠书签共享。  
  
|书签|Text|  
|--------|----------|  
|重叠书签|\[this is {sample\] text.}|  
|Bookmark1|This is sample|  
|Bookmark2|sample text.|  
  
 如果向 Bookmark1 分配新文本“This is replacement.”，则书签不再重叠并且 Bookmark2 仅保留原来不属于 Bookmark1 的文本。  
  
|书签|Text|  
|--------|----------|  
|两个单独的书签|\[this is replacement\]{ text.}|  
|Bookmark1|This is replacement|  
|Bookmark2|text.|  
  
 当一个书签完全包含在另一个书签中时，更改外部书签的文本不会删除内部书签。 但是，内部书签将变成空书签并移动到外部书签的末尾。 下表说明句子“This is sample text.” 如何由包含于另一个书签中的书签共享。  
  
|书签|Text|  
|--------|----------|  
|重叠书签|\[this is {sample} text.\]|  
|Bookmark1|This is sample text.|  
|Bookmark2|示例|  
  
 如果向 Bookmark1 分配新文本“This is replacement.”，则书签不再重叠并且 Bookmark2 变成位于 Bookmark1 末尾的空书签。  
  
|书签|Text|  
|--------|----------|  
|两个单独的书签|\[this is replacement.\]{}|  
|Bookmark1|This is replacement.|  
|Bookmark2|*\<空\>*|  
  
## 事件  
 以下事件可用于 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件：  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## 请参阅  
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [如何：向 Word 文档添加书签控件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [演练：创建书签的快捷菜单](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  