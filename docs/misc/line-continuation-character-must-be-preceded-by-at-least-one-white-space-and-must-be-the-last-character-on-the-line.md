---
title: "行继续符 &quot;_&quot; 的前面必须至少有一个空格，而且必须是所在行中的最后一个字符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30999"
  - "bc30999"
helpviewer_keywords: 
  - "BC30999"
ms.assetid: 32caf62f-52e4-4acd-b40f-5af65e42e643
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 行继续符 &quot;_&quot; 的前面必须至少有一个空格，而且必须是所在行中的最后一个字符
可以在文件中使用下划线 \(\_\) 行继续符将一个长代码行分为若干行。 该下划线必须紧跟在空格后，并且在它后面紧跟行终止符（回车）。 例如:  
  
```  
Dim books As XDocument = _ XDocument.Load(My.Application.Info.DirectoryPath & _ "\..\..\Data\books.xml")  
```  
  
 **错误 ID：**BC30999  
  
### 更正此错误  
  
1.  确保行继续符 \(\_\) 是代码行上的最后一个字符。  
  
2.  确保行继续符前面有一个空格，以便将其与所在行的其他所有代码分开。  
  
## 请参阅  
 [如何：在代码中拆分和合并语句](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)