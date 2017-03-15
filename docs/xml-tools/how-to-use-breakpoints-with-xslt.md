---
title: "如何：在 XSLT 中使用断点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 如何：在 XSLT 中使用断点
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在 XSLT 样式表中或 XML 源文档中设置断点。如果在标记上设置了断点，则在开始执行时，断点将转到包含源代码行信息的下一条语句。  
  
 有关更多信息，请参见[Debugging Basics: Breakpoints](http://msdn.microsoft.com/zh-cn/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)。  
  
## 在样式表中设置断点  
 在 XSLT 样式表的开始标记、结束标记和文本节点上都可以设置断点。也可以在脚本块中的代码上设置断点。  
  
#### 在样式表中设置断点  
  
1.  在“XML 编辑器”中打开样式表。  
  
2.  将光标置于断点位置，右击并指向“断点”，再单击“插入断点”。  
  
3.  在文档属性窗口的**“输入”**字段上单击“浏览”按钮 \(**...**\)。  
  
4.  找到 XML 源文档并单击**“打开”**。  
  
     此时将设置用于 XSLT 转换的源文档文件。  
  
5.  在“XML 编辑器”的工具栏上单击**“调试 XSL”**按钮。  
  
## 在 XML 源文档中设置断点  
 在 XML 源文档的元素、属性、命名空间节点、注释、处理指令和文本节点上都可以设置断点。无法在文档节点上或在继承自父元素的命名空间节点设置断点。  
  
#### 在 XML 源文档中设置断点  
  
1.  在 XML 编辑器中打开 XML 文档。  
  
2.  将光标置于断点位置，右击并指向“断点”，再单击“插入断点”。  
  
3.  在文档属性窗口的**“样式表”**字段上单击“浏览”按钮 \(**...**\)。  
  
4.  找到 XML 源文档并单击**“打开”**。  
  
     此时将设置用于 XSLT 转换的源文档文件。  
  
5.  在“XML 编辑器”的工具栏上单击**“调试 XSL”**按钮。  
  
## 请参阅  
 [演练：调试 XSLT 样式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)