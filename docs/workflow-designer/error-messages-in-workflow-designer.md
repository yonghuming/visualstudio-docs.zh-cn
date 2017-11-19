---
title: "工作流设计器中的错误消息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef4e1883fd6f72ab0937f4b6502c6bad086eb68f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="error-messages-in-workflow-designer"></a>工作流设计器中的错误消息
本主题介绍在使用 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 时可能遇到的错误消息的类型。  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>工作流设计器中出现错误的情况  
 在以下情况下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中会出现错误：  
  
1.  表达式中存在错误。  
  
2.  活动的验证约束未满足。  
  
3.  XAML 文件中存在错误，导致活动无法加载。  
  
4.  XAML 文件中存在错误，导致工作流无法加载。  
  
 无效的表达式和未满足的验证约束不会导致工作流无法生成。 会成功生成工作流，但在运行时将引发 <xref:System.Activities.InvalidWorkflowException>。 如果 XAML 文件中存在错误，生成将失败。  
  
 内部[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，当加载工作流时，其错误都显示在**错误列表**。 若要导航到错误的源的活动，双击中的错误**错误列表**。  
  
### <a name="expression-errors"></a>表达式错误  
 无效表达式用红色圆圈表示，并且该表达式旁有一个白色感叹号。 悬停在此图标上将显示描述错误来源的工具提示。 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内，单击该表达式可查看对错误来源加下划线的行。 悬停在此加下划线的文本上将显示描述错误来源的工具提示。  
  
### <a name="activity-validation-errors"></a>活动验证错误  
 活动的验证约束未满足时，红色圆圈及白色感叹号显示在该活动的右上角。 悬停在此图标上将显示描述错误来源的工具提示。  
  
### <a name="xaml-load-errors"></a>XAML 加载错误  
 当活动失败时加载时，将显示一个红框以文本"活动无法加载由于 XAML 中的错误"。 这通常发生在无法解析活动的类型。 可以在设计器中删除无效的活动，方法是选中红色框，然后删除它。  
  
### <a name="workflow-load-errors"></a>工作流加载错误  
 当工作流失败时加载时，文本"工作流设计器遇到问题与您的文档"将显示在设计器图面，以及导致工作流加载失败的异常信息。 这通常发生在无法分析 XAML 文件时。