---
title: "Rethrow 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a41dd3b640b53689f8eb3ef3c0a02cd3e191df7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="rethrow-activity-designer"></a>Rethrow 活动设计器
**重新引发**活动设计器用于创建和配置<xref:System.Activities.Statements.Rethrow>活动。  
  
## <a name="the-rethrow-activity"></a>Rethrow 活动  
 <xref:System.Activities.Statements.Rethrow> 活动引发先前已引发的异常。 此活动只能在 <xref:System.Activities.Statements.Catch> 活动的 <xref:System.Activities.Statements.TryCatch> 处理程序中使用。  
  
### <a name="using-the-rethrow-activity-designer"></a>使用 ReThrow 活动设计器  
 **重新引发**在找不到活动设计器**错误处理**类别**工具箱**，通过单击访问的哪一**工具箱**的左侧选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单或 CTRL + ALT + X。)  
  
 **重新引发**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建<xref:System.Activities.Statements.Rethrow>默认值的活动**DisplayName**引发。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑值**重新引发**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-rethrow-properties"></a>Rethrow 属性  
 下表列出 <xref:System.Activities.Statements.Rethrow> 属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Rethrow> 活动的可选友好名称。 默认值为 Rethrow。|  
  
## <a name="see-also"></a>另请参阅  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [引发](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)