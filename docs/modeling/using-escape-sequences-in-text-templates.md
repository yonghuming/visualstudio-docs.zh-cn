---
title: "在文本模板中使用转义序列 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fdf062c9b33dd4a160f54bba83991a3cdda7f0d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="using-escape-sequences-in-text-templates"></a>在文本模板中使用转义序列
你可以在文本模板生成文本模板标记和 （在 C# 仅在代码中） 使用转义序列转义控制字符和引号引起来。  
  
 若要打印的输出文件的标准的代码块的打开和关闭标记，请转义标记，如下所示：  
  
```  
\<# ... \#>  
```  
  
 你可以执行相同，但有其他文本模板指令和代码块标记。  
  
 如果文本块包括用于转义文本模板标记的字符串，你可以使用以下的转义序列：  
  
-   如果文本模板标记前面带有转义为偶数 (\\) 字符模板分析器将包括一半的转义字符并将包含为文本模板标记序列。 例如，如果文本模板中有四个转义字符，将有两个"\\"生成文件中的字符。  
  
-   如果文本模板标记前面带有转义为奇数 (\\) 字符，则模板分析器将包括的下半部分"\\"字符以及标记本身 (\<# 或 #>)。 标记不被视为是一个文本模板标记。  
  
-   如果转义 (\\) 字符显示其中一个控制字符或引号 （仅在 C#) 进行转义以外的任何序列中的其他任何位置，将直接输出的字符。  
  
## <a name="see-also"></a>另请参阅  
 [如何：使用转义序列基于模板生成模板](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)