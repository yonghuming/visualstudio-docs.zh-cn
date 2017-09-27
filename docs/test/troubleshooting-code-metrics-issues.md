---
title: "代码度量值问题疑难解答 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: erickson-doug
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 26dc2869ceb16e2c16a74ee52249777394fb666a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="troubleshooting-code-metrics-issues"></a>代码度量值问题疑难解答
收集代码度量值时，可能遇到的一些以下问题：  
  
-   [Visual Studio 2010 代码复杂性计算中的更改](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Visual Studio 2010 代码复杂性计算中的更改  
 对于相同的函数中，代码复杂性度量值计算中[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]可以不同于早期版本的计算的度量值[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]在以下情况下：  
  
-   该函数包含一个或多个 catch 块。 在以前版本的[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，catch 块中不包含在计算中使用。 在[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]，每个 catch 块的复杂性添加到该函数的复杂性。  
  
-   该函数包含 switch (在 VB 中的 Select Case) 语句。 编译器之间的差异[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]和早期版本可以生成包含回退通过情况下某些 switch 语句的不同 MSIL 代码。  
  
## <a name="see-also"></a>另请参阅  
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
