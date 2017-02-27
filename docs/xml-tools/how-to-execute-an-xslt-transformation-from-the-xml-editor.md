---
title: "如何：在 XML 编辑器中执行 XSLT 转换 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 如何：在 XML 编辑器中执行 XSLT 转换
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过 XML 编辑器可以将 XSLT 样式表与 XML 文档关联，执行转换，以及查看输出。由 XSLT 转换生成的输出显示在新的文档窗口中。  
  
 “输出”属性指定输出的文件名。如果“输出”属性为空白，则在临时目录中生成一个文件名。文件扩展名基于样式表中的 `xsl:output` 元素，可以是 .xml、.txt 或 .htm。  
  
 如果“输出”属性指定了扩展名为 .htm 或 .html 的文件名，XSLT 输出将使用 [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer 进行预览。所有其他文件扩展名将使用 [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio 选择的默认编辑器打开。例如，如果文件扩展名为 .xml，Visual Studio 将使用“XML 编辑器”。  
  
### 从 XML 文档执行 XSLT 转换  
  
1.  在“XML 编辑器”中打开 XML 文档。  
  
2.  将 XSLT 样式表与 XML 文档关联。  
  
    -   将 `xml-stylesheet` 处理指令添加到 XML 文档中。例如，将以下行 `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` 添加到文档序言中。  
  
         \- 或 \-  
  
    -   使用“属性”窗口添加 XSLT 样式表。在文档的“属性”窗口中，单击“样式表”字段的“浏览”按钮，选择 XSLT 样式表，再单击“打开”。  
  
3.  在“XML 编辑器”的工具栏上单击“显示 XSL 输出”按钮。  
  
    > [!NOTE]
    >  如果没有与 XML 文档关联的样式表，对话框会提示您提供要使用的样式表。  
    >   
    >  由 XSLT 转换生成的输出显示在新的文档窗口中。  
  
### 从 XSLT 样式表执行 XSLT 转换  
  
1.  在“XML 编辑器”中打开 XSLT 样式表。  
  
2.  在文档“属性”窗口的“输入”字段中指定 XML 文档。  
  
    > [!NOTE]
    >  XML 文档是用于转换的输入文档。如果在 XSLT 转换开始时未指定文档，“文件打开”对话框将出现，可以在此时指定文档。  
  
3.  在“XML 编辑器”的工具栏上单击“显示 XSLT 输出”按钮。  
  
     由 XSLT 转换生成的输出显示在新的文档窗口中。  
  
### 提供不同的输出文件名  
  
1.  在文档“属性”窗口的“输出”字段中指定文件名。  
  
2.  在“XML 编辑器”的工具栏上单击“显示 XSLT 输出”按钮。  
  
     由 XSLT 转换生成的输出显示在新的文档窗口中，输出窗口中使用的编辑器取决于“输出”文档属性的文件扩展名。  
  
## 请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)