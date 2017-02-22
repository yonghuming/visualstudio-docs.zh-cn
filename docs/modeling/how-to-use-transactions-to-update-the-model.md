---
title: "如何：使用事务更新模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 7
caps.handback.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 如何：使用事务更新模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

事务，以确保对存储的更改将组。  更改分组可以提交或回滚作为一个单元。  
  
 每当程序代码在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可视化的存储修改，添加或删除所有元素和建模 SDK，则必须先在事务内。  ，当发生更改时，必须具有 <xref:Microsoft.VisualStudio.Modeling.Transaction> 有效的实例与存储。  这适用于任何模型元素、关系、形状、关系图及其特性。  
  
 事务机制可帮助您避免不一致的状态。  如果错误在事务中生成，滚全部更改。  如果用户执行一个取消命令，每个最新事务将单个步骤。  ，除非在单独的事务，显式将它们放置用户无法撤消最近更改的部分。  
  
## 打开事务  
 管理事务最方便的方法与 `try...catch` 语句中的 `using` 语句:  
  
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
  
 在更改期间，如果防止最终 `Commit()`的异常，存储将重置为其以前的状态。  这有助于确保，错误处于不一致状态不能使该模型保留。  
  
 您可以在一个事务内的任意数量的更改。  可以在一个活动事务内的新事务。  嵌套事务必须在包含的事务结束之前提交或回滚。  有关更多信息，请 <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> 属性请参见示例。  
  
 ，在它之前，使更改永久，应 `Commit` 事务。  如果没有捕获在事务内发生异常，存储将重置为其更改前的状态。  
  
## 回滚事务  
 若要确保存储保持在或还原为其状态在事务之前，可以使用这些策略之一:  
  
1.  引发了未捕获在该事务范围内的异常。  
  
2.  请显式回滚事务:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## 事务不影响非存储对象  
 事务只有管理存储 " 状态。  它们不能撤消对外部项 \(如文件、数据库或对象中声明了在 DSL 定义之外的普通类型的部分更改。  
  
 如果异常可能将此类更改不一致存储区，则应处理在异常处理程序的可能性。  一种方法，以确保外部资源保持与存储对象同步将与一个仓库元素的每个外部对象使用事件处理程序。  有关更多信息，请参见 [事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
## 规则。在事务末尾  
 在事务结束时，，在事务之前，规则附加到组件在存储会激发。  每个规则是应用于模型元素已更改的方法。  例如，具有 “修复”更新形状状态的规则，其模型元素更改时，因此，创建形状，当一个模型元素之后。  未指定的引发顺序。  规则所做的更改可能引发另一规则。  
  
 可以定义拥有规则。  有关规则的更多信息，请参见[响应并传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
 规则将引发，取消、重新提交或回滚命令之后。  
  
## 事务上下文  
 每个事务可以存储所有信息所需的字典:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 这对于调用信息是尤为有用。规则。  
  
## 事务状态  
 有时需要避免将更改传播更改，则由撤消或重做事务导致的。  这可能发生，例如，因此，如果您编写可更新其他值在存储属性值的处理程序。  因撤消操作重置所有值都存储到之前的状态，计算更新值并不是必需的。  使用此代码:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 规则会激发存储在从文件最初加载。  若要避免响应这些更改，请使用:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```