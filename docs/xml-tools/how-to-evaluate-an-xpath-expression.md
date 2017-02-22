---
title: "如何：计算 XPath 表达式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：计算 XPath 表达式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用“快速监视”对话框计算 XPath 表达式。XPath 表达式必须符合 W3C XPath 1.0 建议。当前 XSLT 上下文 — 即“局部变量”窗口中的 `self::node()` 节点 — 为 XPath 表达式提供计算上下文。  
  
 下表说明在计算 XPath 表达式时支持的函数：  
  
-   支持内置 XPath 函数。  
  
-   不支持内置 XSLT 函数。  
  
-   不支持用户定义函数。  
  
> [!NOTE]
>  以下步骤使用[演练：调试 XSLT 样式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)主题中的 belowAvg.xsl 和 books.xml 文件。  
  
### 计算 XPath 表达式  
  
1.  在 `xsl:if` 开始标记处插入断点。  
  
2.  在“XML 编辑器”的工具栏上单击“调试 XSL”按钮。  
  
     调试程序在 `xsl:if` 标记处开始和中断。  
  
3.  右击并选择“快速监视”。  
  
     此时出现“快速监视”对话框。  
  
4.  在“快速监视”对话框的“表达式”字段中输入 `./price/text()`，再单击“重新计算”。  
  
     当前 book 节点的价格将出现在“值”框中。  
  
5.  将 XPath 表达式更改为 `./price/text() < $bookAverage`，再单击**“重新计算”**。  
  
     “值”框显示 XPath 表达式的计算结果为 `true`。  
  
## 请参阅  
 [调试 XSLT](../xml-tools/debugging-xslt.md)