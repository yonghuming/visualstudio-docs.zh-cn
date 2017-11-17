---
title: "如何： 使用事务来更新模型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: "7"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 3fdf24bbcfcbda2e5e6c1d8a3737d9a53ed5ae23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-transactions-to-update-the-model"></a>如何：使用事务更新模型
事务确保对应用商店所做的更改被视为一个组。 可以提交或回滚作为单个单元进行分组的更改。  
  
 每当程序代码中修改、 添加，或删除中的存储区中的任意元素[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可视化和建模 SDK，它必须在事务内执行此操作。 必须有的活动实例<xref:Microsoft.VisualStudio.Modeling.Transaction>发生更改与存储相关联。 这适用于所有模型元素、 关系、 形状、 关系图和其属性。  
  
 事务机制可帮助你避免不一致的状态。 如果在事务期间发生错误，将回滚所有更改。 如果用户执行撤消命令时，每个新的事务将被视为单个步骤。 除非你显式将它们放在单独的事务，则用户无法撤消最近更改的部分。  
  
## <a name="opening-a-transaction"></a>打开事务  
 管理事务的最方便的方法是借助`using`语句括在`try...catch`语句：  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 如果异常阻止最终`Commit()`过程中发生更改，存储将重置为其以前的状态。 这有助于确保错误不会处于不一致状态中离开模型。  
  
 你可以在一个事务内的更改的任何数。 你可以打开在活动事务内的新事务。 嵌套的事务必须提交或回滚在包含事务结束之前。 有关详细信息，请参阅示例<xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>属性。  
  
 若要使所做的更改为永久更改，你应`Commit`事务之前已释放。 如果异常发生在事务捕获不到，存储将重置为其状态之前所做的更改。  
  
## <a name="rolling-back-a-transaction"></a>回滚事务  
 若要确保应用商店处于或将恢复为其状态的事务处理前，可以使用这些策略之一：  
  
1.  引发在事务范围内未被捕获的异常。  
  
2.  显式回滚事务：  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>事务不会影响非存储对象  
 事务仅控制的存储区的状态。 它们不能撤消部分如文件、 数据库或具有使用普通类型 DSL 定义之外声明的对象的外部项所做的更改。  
  
 如果异常可能会将此类更改与应用商店不一致，您应处理的异常处理程序在这种可能性。 请确保外部资源保持同步的存储对象的一种方法是通过使用事件处理程序将与存储区中元素的每个外部对象。 有关详细信息，请参阅[事件处理程序传播更改外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>在事务结束规则激发  
 在事务结束时，释放事务之前，会触发附加到存储区中的元素的规则。 每个规则是应用到模型元素已更改的方法。 例如，有"修复"的规则，更新形状的状态时其模型元素已更改，并创建模型元素时，其创建的形状。 没有任何指定的激发顺序。 由规则所做的更改可能会引发另一个规则。  
  
 你可以定义自己的规则。 有关规则的详细信息，请参阅[响应和传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
 规则不会触发后已撤消、 重做或回滚命令。  
  
## <a name="transaction-context"></a>事务上下文  
 每个事务都有一个字典可以在其中存储所需的任何信息：  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 这是特别有用的规则之间传输信息。  
  
## <a name="transaction-state"></a>事务状态  
 在某些情况下，你需要避免传播更改，如果更改由撤消或重做事务。 这可能发生，例如，如果您编写的属性值处理程序可以更新存储区中的另一个值。 撤消操作将存储区中的所有值重都置为其之前的状态，因为它不需要计算更新后的值。 使用此代码：  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 应用商店最初从文件加载时，规则可以激发。 若要避免对这些更改作出响应，请使用：  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```