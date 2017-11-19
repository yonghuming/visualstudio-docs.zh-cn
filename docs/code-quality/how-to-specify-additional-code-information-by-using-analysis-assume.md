---
title: "如何： 使用 __analysis_assume 指定其他代码信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __analysis_assume
helpviewer_keywords: __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 72892328e9e0cd2f85176cfc4a514d64f853d209
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>如何：使用 __analysis_assume 指定其他代码信息
C/c + + 代码，它们将帮助分析过程并降低警告，你可以提供对代码分析工具提示。 若要提供的其他信息，请使用以下函数：  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`-假定才能评估为 true 的任何表达式。  
  
 代码分析工具假定表达式所表示的条件为 true 的点，其中该函数将显示并将保持为 true，直到表达式更改了，例如，通过对变量赋值。  
  
> [!NOTE]
>  `__analysis_assume`不会影响代码优化。 代码分析工具，外部`__analysis_assume`指不执行任何操作。  
  
## <a name="example"></a>示例  
 下面的代码使用`__analysis_assume`更正代码分析警告[C6388](../code-quality/c6388.md):  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [__assume](/cpp/intrinsics/assume)