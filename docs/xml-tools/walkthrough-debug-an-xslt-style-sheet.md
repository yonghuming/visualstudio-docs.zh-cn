---
title: "演练：调试 XSLT 样式表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 演练：调试 XSLT 样式表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此演练中的步骤演示如何使用 XSLT 调试程序。步骤包括查看变量、设置断点和逐行执行代码。样式表查找所有价格低于平均书价的书籍。  
  
### 准备此次演练  
  
1.  关闭任何打开的解决方案。  
  
2.  将两个示例文件复制到本地计算机上。  
  
## 开始调试  
  
#### 要开始调试，请执行下列操作：  
  
1.  从“文件”菜单中指向“打开”，然后单击“文件”。  
  
2.  找到 belowAvg.xsl 文件并单击“打开”。  
  
     该样式表将在“XML 编辑器”中打开。  
  
3.  在文档属性窗口的“输入”字段上单击“浏览”按钮 \(**...**\)。  
  
4.  找到 books.xml 文件并单击“打开”。  
  
     此时将设置用于 XSLT 转换的源文档文件。  
  
5.  右击 `xsl:if` 开始标记，指向“断点”，再单击“插入断点”。  
  
6.  在“XML 编辑器”的工具栏上单击“调试 XSL”按钮。  
  
 此时将开始调试过程，并打开几个新窗口供调试程序使用。  
  
 有两个窗口显示输入文档和样式表。调试器使用这些窗口来显示当前的执行状态。调试器位于样式表的 `xsl:if` 元素上和 books.xml 文件中的第一个 book 节点上。  
  
 “局部变量”窗口显示所有局部变量及其当前值。其中包括样式表中定义的变量，也包括调试程序在跟踪上下文中的当前节点时使用的变量。  
  
 “XSL 输出”窗口显示 XSL 转换的输出。此窗口独立于“Visual Studio 输出”窗口。  
  
## “监视”窗口  
  
#### 要使用“监视”窗口，请执行下列操作：  
  
1.  在“调试”菜单中指向“窗口”，再指向“监视”，然后单击“监视 1”。  
  
     此时出现“监视 1”窗口。  
  
2.  在“名称”字段中键入 `$bookAverage`，再按 ENTER 键。  
  
     `$bookAverage` 变量的值将显示在窗口中。  
  
3.  在“名称”字段中键入 `self::node()`，再按 ENTER 键。  
  
     `self::node()` 是一个计算结果为当前上下文节点的 XPath 表达式。`self::node()` XPath 表达式的值是第一个 book 节点。此值随着转换的进度而更改。  
  
4.  展开 `self::node()` 节点，然后展开 `price` 节点。  
  
     这样可以查看书价的值，并且可以很容易将其与 `$bookAverage` 值进行比较。因为书价低于平均值，所以，`xsl:if` 条件应继续。  
  
## 逐行执行代码  
 调试程序允许您一次执行一行代码。  
  
#### 要逐行执行代码，请执行下列操作：  
  
1.  按 **F5** 键继续。  
  
     因为第一个 book 节点满足 `xsl:if` 条件，所以，该 book 节点将添加到“XSL 输出”窗口。调试器继续执行，直到它再次位于样式表中的 `xsl:if` 元素上。调试器此时位于 books.xml 文件中的第二个 book 节点上。  
  
     在 Watch1 窗口中，`self::node()` 值变为第二个 book 节点。通过检查 price 元素的值，可以确定价格高于平均值，所以，`xsl:if` 条件应失败。  
  
2.  按 **F5** 键继续。  
  
     因为第二个 book 节点未满足 `xsl:if` 条件，所以不会将此 book 节点添加到“XSL 输出”窗口。调试器继续执行，直到它再次位于样式表中的 `xsl:if` 元素上。调试器此时位于 books.xml 文件中的第三个 `book` 节点上。  
  
     在 Watch1 窗口中，`self::node()` 值变为第三个 book 节点。通过检查 `price` 元素的值，您可以确定此价格低于平均价格，因此 `xsl:if` 条件应成立。  
  
3.  按 **F5** 键继续。  
  
     因为满足 `xsl:if` 条件，所以，第三个 book 节点将添加到“XSL 输出”窗口。XML 文档中的所有 book 节点均已处理，调试程序停止。  
  
## 示例文件  
 下列两个文件供该演练使用。  
  
### belowAvg.xsl  
  
```  
<?xml version='1.0'?>  
<xsl:stylesheet version="1.0"  
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:output method="xml" encoding="utf-8"/>  
  <xsl:template match="/">  
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>  
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>  
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>  
    <books>  
      <!--Books That Cost Below Average-->  
      <xsl:for-each select="/bookstore/book">  
        <xsl:if test="price < $bookAverage">  
          <xsl:copy-of select="."/>  
        </xsl:if>  
      </xsl:for-each>  
    </books>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### books.xml  
  
```  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database -->  
<bookstore>  
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">  
    <title>The Autobiography of Benjamin Franklin</title>  
    <author>  
      <first-name>Benjamin</first-name>  
      <last-name>Franklin</last-name>  
    </author>  
    <price>8.99</price>  
  </book>  
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">  
    <title>The Confidence Man</title>  
    <author>  
      <first-name>Herman</first-name>  
      <last-name>Melville</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">  
    <title>The Gorgias</title>  
    <author>  
      <name>Plato</name>  
    </author>  
    <price>9.99</price>  
  </book>  
</bookstore>  
```  
  
## 请参阅  
 [调试 XSLT](../xml-tools/debugging-xslt.md)