---
title: "对锁定行为进行批注 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 对锁定行为进行批注
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要避免多线程程序中的并发 Bug，请遵循相应的锁定并使用 SAL 注释。  
  
 并发 Bug 公认的难以重现，诊断和调试，因为它们是非确定性的。  有关跨线程很难达到最佳的原因，以及当设计包含有很多线程代码体时变得不切实际的原因。  因此，在多线程程序中最好遵循的锁定规则。  例如，它们在获取多个锁时遵守锁定顺序，可以帮助避免死锁，并在访问共享资源之前获取适当的保护锁可以帮助阻止争用条件。  
  
 遗憾的是，在实践中似乎简单的锁可能会惊奇地难遵循  在当今编程语言和编译器的一个基础限制是根本不直接支持并发要求规范和分析。  程序员必须依赖于非正式的代码注释表示有关他们如何使用锁定的本意。  
  
 并发 SAL 注释用于帮助您指定锁的副作用，锁的责任，数据保护，锁的层次顺序，以及其他的期望的锁行为。  通过隐式制定规则，SAL 并发注释提供了一个一致方式说明在文档代码锁如何使用的规则。  并发注释还增强了代码分析工具查找争用条件、死锁，、不匹配的同步操作和其他细微并发错误的能力。  
  
## 通用准则  
 使用注释，您可以按照在实现 \(被调用方\) 和客户端 \(调用方\) 之间的函数定义的隐式协议，并表达可以使程序进一步改进分析的约束条件和其他属性。  
  
 SAL 支持许多不同的基元锁定如示例、临界区、互斥锁、自旋锁和其他资源对象。  许多并发说明采用锁表达式作为参数。  按照约定，锁由基础锁对象的路径的表达式表示。  
  
 记住某些线程所有权的规则：  
  
-   自旋锁是具有明确所有权的线程的非计数锁。  
  
-   互斥锁和关键部分是具有明确所有权的线程的计数锁。  
  
-   信号量和事件是不具有明确线程所有权的锁计数。  
  
## 锁定批注  
 下表列出了锁注释。  
  
|批注|说明|  
|--------|--------|  
|`_Acquires_exclusive_lock_(expr)`|注释的函数意味着在后置状态该函数的递增由一个由 `expr`命名的锁对象的专用锁计数。|  
|`_Acquires_lock_(expr)`|注释的函数意味着在后置状态该函数的递增由一个由 `expr`命名的锁对象的锁计数。|  
|`_Acquires_nonreentrant_lock_(expr)`|由 `expr` 命名的锁已获得。如果锁已持有，会报告错误。|  
|`_Acquires_shared_lock_(expr)`|在后置状态注释的函数意味着该函数的递增由一个由 `expr`命名的锁对象的共享锁计数。|  
|`_Create_lock_level_(name)`|该语句声明符号 `name` 为锁级别，以便可以在注释 `_Has_Lock_level_` 和 `_Lock_level_order_` 中使用。|  
|`_Has_lock_kind_(kind)`|注释所有对象优化资源对象的类型信息。  有时一常见类型会用于不同类型的资源，并且重载的类型不足以区分各资源之间的语义要求。  这有一个预定义`kind`的参数列表：<br /><br /> `_Lock_kind_mutex_`<br /> 互斥锁的锁类型 ID。<br /><br /> `_Lock_kind_event_`<br /> 事件的锁类型 ID。<br /><br /> `_Lock_kind_semaphore_`<br /> 信号量的锁类型 ID。<br /><br /> `_Lock_kind_spin_lock_`<br /> 自旋锁的锁类型 ID。<br /><br /> `_Lock_kind_critical_section_`<br /> 临界区的锁类型 ID。|  
|`_Has_lock_level_(name)`|注释锁对象并赋予其锁级别为 `name`。|  
|`_Lock_level_order_(name1, name2)`|该语句给出此锁在 `name1` 和 `name2` 之间的排序。|  
|`_Post_same_lock_(expr1, expr2)`|注释的函数意味着在后置状态的两种锁定 `expr1`，并且 `expr2` 被视为相同的锁对象。|  
|`_Releases_exclusive_lock_(expr)`|注释的函数意味着在后置状态该函数的递减由一个由 `expr`命名的锁对象的专用锁计数。|  
|`_Releases_lock_(expr)`|注释的函数意味着在后置状态该函数的递减由一个由 `expr`命名的锁对象的锁计数。|  
|`_Releases_nonreentrant_lock_(expr)`|由 `expr` 命名的锁已发布。  目前，如果锁不持有，会报告错误。|  
|`_Releases_shared_lock_(expr)`|注释的函数意味着在后置状态该函数的递减由一个由 `expr`命名的锁对象的共享锁计数。|  
|`_Requires_lock_held_(expr)`|注释的函数意味着之前声明的由 `expr` 命名的对象的锁计数至少为一个。|  
|`_Requires_lock_not_held_(expr)`|注释的函数并意味着之前声明的由 `expr` 命名的对象的锁计数为0个。|  
|`_Requires_no_locks_held_`|注释的函数指示检查器已知所有锁的锁计数为零。|  
|`_Requires_shared_lock_held_(expr)`|注释的函数意味着之前声明的由 `expr` 命名的对象的共享锁计数至少为一个。|  
|`_Requires_exclusive_lock_held_(expr)`|注释的函数意味着之前声明的由 `expr` 命名的对象的专有锁计数至少为一个。|  
  
## 非公开锁定对象的 SAL 内部  
 某些锁对象不被关联的锁函数的实现公开。下表列出可以启用用于操作那些未公开的锁对象函数的注释的 SAL 内部变量。  
  
|批注|说明|  
|--------|--------|  
|`_Global_cancel_spin_lock_`|取消自旋锁描述。|  
|`_Global_critical_region_`|临界区描述。|  
|`_Global_interlock_`|互锁操作描述。|  
|`_Global_priority_region_`|优先级区域描述。|  
  
## 共享数据访问批注  
 下表列出了用于共享数据访问的注释。  
  
|批注|说明|  
|--------|--------|  
|`_Guarded_by_(expr)`|注释变量意味着，每当变量被访问，由 `expr` 命名的锁对象的锁计数至少为一个。|  
|`_Interlocked_`|注释变量与 `_Guarded_by_(_Global_interlock_)`等效。|  
|`_Interlocked_operand_`|注释的函数参数是多联锁函数之一的目标操作数。那些操作数必须具有特定的附加属性。|  
|`_Write_guarded_by_(expr)`|注释变量意味着，每当变量被修改，由 `expr` 命名的锁对象的锁计数至少为一个。|  
  
## 请参阅  
 [使用 SAL 批注以减少 C\/C\+\+ 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [内部函数](../code-quality/intrinsic-functions.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)   
 [Code Analysis Team Blog](http://go.microsoft.com/fwlink/p/?LinkId=251197)