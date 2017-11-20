---
title: "代码分析问题疑难解答 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>代码分析问题疑难解答
本主题包含以下 Visual Studio 代码分析问题的疑难解答信息。  
  
-   [Visual Studio 2010 规则集是不反映在 Visual Studio 早期版本中的更改](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Visual Studio 2010 规则集是不反映在 Visual Studio 早期版本中的更改  
 当创建所设置的规则[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]包含子规则集，则向子规则集的更改可能不会应用在使用 Visual Studio 的早期版本的计算机上的代码分析运行中。 若要解决此问题，必须强制执行重写父规则集，即包含子规则集的规则集。  
  
1.  在中打开父规则设置[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]。  
  
2.  进行更改，如添加或删除规则，然后保存规则集。  
  
3.  重新打开规则集，撤消更改，然后保存该规则集再次。  
  
## <a name="see-also"></a>另请参阅  
 [分析应用程序质量](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [分析托管的代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [使用规则集对代码分析规则进行分组](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)