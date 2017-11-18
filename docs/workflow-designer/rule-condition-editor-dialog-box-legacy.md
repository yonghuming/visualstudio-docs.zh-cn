---
title: "规则条件编辑器对话框 （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords: Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98a42547786e15815ef760e9f397c3c469c4a1a1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>“规则条件编辑器”对话框（旧版）
本主题介绍如何使用**规则条件编辑器**对话框中，在旧[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]。 在需要面向 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
 创建和修改声明性规则条件使用**规则条件编辑器**对话框。 这些规则条件作为以下 Windows Workflow Foundation 现成可用的活动属性被公开：  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 你访问**规则条件编辑器**对话框中，通过使用[选择条件对话框 （旧版）](../workflow-designer/select-condition-dialog-box-legacy.md)。  
  
 下表描述的用户界面 (UI) 元素**规则条件编辑器**对话框。  
  
|UI 元素|描述|  
|----------------|-----------------|  
|**条件：**|为规则条件输入表达式。|  
|**还行**|单击可以保存规则条件。|  
  
## <a name="entering-condition-expressions"></a>输入条件表达式  
 条件表达式是以文本形式输入的。 你可以键入**这。** 若要引用字段、 属性和工作流中使用的方法在编辑器，使用类似于 IntelliSense 的菜单。 或者，可以直接键入工作流成员名称。 可以向条件中添加逻辑运算符（如 AND、OR 和 NOT）。 也可以添加谓词。 谓词由一个二元运算符和两个操作数组成。 支持的二进制运算符是 **==** ，  **>** ，  **\<** ，  **>=** ，和 **<=** 。 支持的操作数包括常量值、算术函数和作用域公共成员。  
  
 你可以指定的类型比较，且您可以比较到**null**或空字符串。 您可以对包含复杂类型的变量进行嵌套的成员调用，例如，`this.Address.State == "WA"`。  
  
 该规则条件编辑器支持以下运算符：  
  
-   关系运算符：==、=、!=  
  
-   比较运算符： <， \<=、 >、 > =  
  
-   算术运算符：+、-、*、/、MOD  
  
-   逻辑运算符:，& &、 OR、 &#124; &#124;、 NOT、 ！  
  
-   按位运算符： &、 &#124;  
  
 表达式运算符优先级遵循 C# 运算符优先级规则。  
  
 该规则条件编辑器支持以下数值表达式：  
  
 this.i == 1D（解析为 1.0）  
  
 this.i == 1E1（解析为 10.0）  
  
 this.i == 1L（解析为 long 类型值）  
  
 this.i == 1M（解析为 decimal 类型值）  
  
 this.i == 1F（解析为 single 类型值）  
  
 this.i == 1U（解析为 unsigned int 类型值）  
  
 有关条件的详细信息，请参阅[在工作流中使用条件](http://go.microsoft.com/fwlink?LinkID=65009)。  
  
## <a name="see-also"></a>另请参阅  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [选择条件对话框 （旧版）](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [工作流中使用条件](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Windows Workflow Foundation 的旧版设计器 UI 帮助](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)