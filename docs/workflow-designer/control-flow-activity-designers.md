---
title: "控制流活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 控制流活动设计器
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 包含系统提供的若干活动，构造工作流时可以使用它们。本节包含系统提供的活动中用于控制工作流中的流的活动。以下主题介绍这些活动以及如何使用它们。  
  
## 本节内容  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 执行其主体中包含的活动至少一次，直到指定条件的计算结果为 **true**。  
  
 [ForEach\<T\>](http://msdn.microsoft.com/zh-cn/a680cddd-2760-497a-b27b-c023fcbc6f33)  
 为指定集合中的每一项执行其主体中包含的活动。  
  
 [If](../workflow-designer/if-activity-designer.md)  
 计算条件并根据该计算结果执行活动。  
  
 [Parallel](../workflow-designer/parallel-activity-designer.md)  
 并发执行一组子活动。  
  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)  
 枚举集合元素并对集合中的每个元素并行执行嵌入语句。  
  
 [Pick](../workflow-designer/pick-activity-designer.md)  
 执行多个分支中的一个分支来响应某个事件，它提供了基于事件的流控制。  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 提供了 <xref:System.Activities.Statements.Pick> 活动中的可能执行路径。  
  
 [Sequence](../workflow-designer/sequence-activity-designer.md)  
 包含子活动的已排序集合，将按该排序执行这些子活动。  
  
 [Switch\<T\>](http://msdn.microsoft.com/zh-cn/ce1aa634-c4db-4475-a1c8-a88478a57212)  
 计算指定表达式并执行活动集合中其关联键与计算所得值匹配的活动。  
  
 [While](../workflow-designer/while-activity-designer.md)  
 当指定条件的计算结果为 **true** 时，执行该活动主体中包含的活动。  
  
## 参考  
 <xref:System.Activities.Activity>  
  
 <xref:System.Activities.Statements.DoWhile>  
  
 <xref:System.Activities.Statements.ForEach%601>  
  
 <xref:System.Activities.Statements.If>  
  
 <xref:System.Activities.Statements.Parallel>  
  
 <xref:System.Activities.Statements.ParallelForEach%601>  
  
 <xref:System.Activities.Statements.Pick>  
  
 <xref:System.Activities.Statements.PickBranch>  
  
 <xref:System.Activities.Statements.Sequence>  
  
 <xref:System.Activities.Statements.Switch%601>  
  
 <xref:System.Activities.Statements.While>  
  
## 相关章节  
 有关其他类型活动设计器的信息，请参见下列主题。  
  
 [使用活动设计器](../workflow-designer/using-the-activity-designers.md)  
  
 [流程图](../workflow-designer/flowchart-activity-designers.md)  
  
 [消息传送](../workflow-designer/messaging-activity-designers.md)  
  
 [运行时](../workflow-designer/runtime-activity-designers.md)  
  
 [基元](../workflow-designer/primitives-activity-designers.md)  
  
 [事务](../workflow-designer/transaction-activity-designers.md)  
  
 [集合](../workflow-designer/collection-activity-designers.md)  
  
 [错误处理](../workflow-designer/error-handling-activity-designers.md)  
  
## 外部资源  
 [使用活动设计器](../workflow-designer/using-the-activity-designers.md)