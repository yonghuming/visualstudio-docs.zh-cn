---
title: "DoWhile 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 43a55a8873fa10fb31db89364c50e084cd72fb5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-activity-designer"></a>DoWhile 活动设计器
<xref:System.Activities.Statements.DoWhile>活动执行中包含的活动其<xref:System.Activities.Statements.DoWhile.Body%2A>至少一次，直到指定的条件的计算结果为**false**。 如果需要执行循环体中包含的活动零次或多次，请改用 <xref:System.Activities.Statements.While> 活动。  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流设计器中的 DoWhile 属性  
 下表列出最有用的 <xref:System.Activities.Statements.DoWhile> 活动属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|要执行的条件时的活动**true**。 若要添加<xref:System.Activities.Statements.DoWhile.Body%2A>活动，将活动从工具箱拖到**正文**框**DoWhile**带提示文本"此处放置活动"的活动设计器。|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|每次循环迭代后要计算的条件。 若要设置<xref:System.Activities.Statements.DoWhile.Condition%2A>，键入一个[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]中的表达式**条件**框**DoWhile**活动设计器或在属性网格中。|  
  
## <a name="see-also"></a>另请参阅  
 [While](../workflow-designer/while-activity-designer.md)   
 [控制流](../workflow-designer/control-flow-activity-designers.md)