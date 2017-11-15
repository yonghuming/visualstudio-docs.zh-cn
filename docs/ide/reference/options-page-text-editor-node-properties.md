---
title: "“选项”页 ->“文本编辑器”节点属性 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a917167b8e81445d0ec47a1dd44cf74f5d87d4f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="options-page-text-editor-node-properties"></a>“选项”页 ->“文本编辑器”节点属性
本文档描述了与“选项”对话框的“文本编辑器”类别 `DTE.Properties("TextEditor", <Property Page>)` 关联的一些页面（或属性集合）。 每个小节的标题都是用于访问 `Properties` 集合的调用，而每个小节中的表都列出了集合中的属性。  
  
 [控制选项设置](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)中的 Visual Basic 宏演示了如何为“选项”对话框的每个页面显示当前选项和值。  
  
## <a name="general"></a>常规  
 `DTE.Properties("TextEditor", "General")`  
  
|属性项名称|值|描述|  
|------------------------|-----------|-----------------|  
|GoToAnchorAfterEscape|Get/Set (Boolean)|如果为 `True`，当有选定内容时按 Escape 会导致插入点移动到在初始化创建选定内容的操作之前的位置。 如果为 `False`，则将插入点移动到选定内容的另一端。|  
|DragNDropTextEditing|Get/Set (Boolean)|确定是否可以将文本的选定区域从文档中的一个位置拖动到其他位置，以执行复制或剪切/粘贴操作。|  
|HorizontalScrollBar|Get/Set (Boolean)|确定编辑器窗口中是否有水平滚动条。|  
|VerticalScrollBar|Get/Set (Boolean)|确定编辑器窗口中是否有垂直滚动条。|  
|SelectionMargin|Get/Set (Boolean)|确定文本窗格的左侧是否有供特殊选择操作、绘制断点图标等使用的空白。|  
|MarginIndicatorBar|Get/Set (Boolean)|确定是否有分隔文本窗格的左边距和文本窗格主体的竖线。|  
|UndoCaretActions|Get/Set (Boolean)|如果 `True`. 除了修改缓冲区的编辑操作外，撤消操作还包括插入点移动、选择命令等。|  
|AutoDelimiterHighlighting|Get/Set (Boolean)|确定键入结束定界符是否使编辑器突出显示开始定界符。 无论该属性的值如何，编辑器始终以粗体显示开始定界符。|  
|EditorEmulation|Get/Set (Enum)||  
|DetectUTF8WithoutSignature|Get/Set (Boolean)|在文件没有编码签名时检测文件是否使用 UTF-8 编码。|  
|TrackChanges|Get/Set (Boolean)||  
  
## <a name="plain-text"></a>纯文本  
 `DTE.Properties("TextEditor", "PlainText")`  
  
 编辑文本文件时，`PlainText` 编辑器选项会影响编辑器设置。 每种编程语言和每个 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 程序包都有其自身特定的**文本编辑器**设置。 例如，若要查看或更改 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 编辑器设置，请使用 `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`。 对于“SQL 脚本”编辑器设置，请使用 `DTE.Properties("TextEditor", "SQL ")`。  
  
|属性项名称|值|描述|  
|------------------------|-----------|-----------------|  
|AutoListMembers|Get/Set (Boolean)|确定用户在变量引用后面键入句点时是否自动显示可用成员列表。|  
|AutoListParams|Get/Set (Boolean)|确定用户在函数名后面键入“(”时是否自动显示参数列表的说明。|  
|HideAdvancedMembers|Get/Set (Boolean)|确定语句结束是列出所有成员还是仅列出常用成员。|  
|VirtualSpace|Get/Set (Boolean)|确定空格字符是否作为图形显示。 将此属性设置为 `true` 会导致将 `WordWrap` 属性项（位于此列表中）设置为 `false`。|  
|WordWrap|Get/Set (Boolean)|确定视图是否将较长的行在字边界处换行。 将此属性设置为 `true` 会导致将 `VirtualSpace` 属性项（位于此列表中）设置为 `false`。|  
|WordWrapGlyphs|Get/Set (Boolean)|在行的末尾显示标志符号；这表明该行会换到下一行。|  
|EnableLeftClickForURLs|Get/Set (Boolean)|确定编辑器是否为 URL 加下划线，并且是否启用单击鼠标左键时跳转到系统注册的 Web 浏览器中的 URL。|  
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>)|确定缩进样式：“默认”、“智能”或“无”。|  
|TabSize|Get/Set (Long)|表示等于一个制表符的空格数。不能将整数设置在 1 至 60（包含 1 和 60）的范围之外。|  
|InsertTabs|Get/Set (Boolean)|如果为 `True`，则缩进时使用 Tab 字符。|  
|IndentSize|Get/Set (Long)|表示等于一个缩进级别的空格数。 不能将整数值设置在 1 至 60（包含 1 和 60）的范围之外。|  
|ShowLineNumbers|Get/Set (Boolean)|确定核心编辑器文档的视图是否在左边距中显示行号。|  
|ShowNavigationBar|Get/Set (Boolean)|确定下拉列表和按钮是否出现在编辑器窗口的顶部。|  
|CutCopyBlankLines|Get/Set (Boolean)|在选中空行时剪切或复制它们。|  
  
## <a name="see-also"></a>另请参阅  
 [控制选项设置](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [确定“选项”页中属性项的名称](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [“选项”页 ->“环境”节点属性](../../ide/reference/options-page-environment-node-properties.md)   
 [“选项”页 ->“字体和颜色”节点属性](../../ide/reference/options-page-fonts-and-colors-node-properties.md)