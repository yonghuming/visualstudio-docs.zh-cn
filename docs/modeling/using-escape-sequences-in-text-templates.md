---
title: "在文本模板中使用转义序列 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, 转义序列"
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# 在文本模板中使用转义序列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以在文本模板中使用转义序列来生成文本模板标记（仅在 C\# 代码中），并对控制字符和引号进行转义。  
  
 若要将标准代码块的开始标记和结束标记打印到输出文件，请对这些标记进行转义，如下所示：  
  
```  
\<# ... \#>  
```  
  
 可以对其他文本模板指令和代码块标记执行相同操作。  
  
 如果文本块包括用于对文本模板标记进行转义的字符串，则可以使用以下转义序列：  
  
-   如果文本模板标记前面有偶数个转义 \(\\\) 字符，则模板分析器会包括一半转义字符，并包括序列作为文本模板标记。  例如，如果文本模板中有四个转义字符，则生成的文件中会有两个“\\”字符。  
  
-   如果文本模板标记前面有奇数个转义 \(\\\) 字符，则模板分析器会包括一半“\\”字符以及标记本身（\<\# 或 \#\>）。  不会将标记视作文本模板标记。  
  
-   如果某个转义 \(\\\) 字符出现在对控制字符或引号进行转义（仅在 C\# 中）之外的任何序列中的其他任何位置，则会直接输出该字符。  
  
## 请参阅  
 [如何：使用转义序列从模板生成模板](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)