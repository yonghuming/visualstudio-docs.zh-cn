---
title: "如何： 使用自变量设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5093e5561140a0ebff57da1f7c21a8954ee58bb3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-the-argument-designer"></a>如何：使用自变量设计器
与以前版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 相比，该参数设计器使数据流入和流出某个活动更容易。 通过单击访问设计器**参数**设计画布左下角的按钮。 该设计器包含显示在表格窗体和可以按每一列标题排序除外的自变量列表**默认值**列。 每个自变量都包含名称、输入/输出/输入-输出/属性方向、类型和默认表达式值（如果有）。 名称和默认的表达式值都是可编辑的文本字段，类型和方向是下拉项。 [!包括[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)。  
  
### <a name="to-create-a-new-argument"></a>创建新自变量  
  
1.  在 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 中打开一个工作流或活动解决方案。  
  
2.  通过单击打开参数设计器**参数**设计画布左下角的按钮。 此时将显示自变量设计器。  
  
3.  单击标记为空的行**创建自变量**。 这会将新行添加使用新的自变量使用以下默认值： 为 argumentx**名称**其中 x 是一个整数，它自动递增，从而创建唯一的自变量名称的 1 的初始值**中**为**方向**，和**字符串**为**自变量类型**。 为添加任何值**默认值**。 可以在工作流设计过程中随时更改这些值。  
  
    > [!NOTE]
    >  若要删除某个参数，通过单击选择的参数，然后按**删除**密钥。  
  
## <a name="see-also"></a>另请参阅  
 [使用工作流设计器](../workflow-designer/using-the-workflow-designer.md)   
 [变量和参数](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)