---
title: "CA2211：非常量字段不应是可见的 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2211：非常量字段不应是可见的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|类别|Microsoft.Usage|  
|是否重大更改|是|  
  
## 原因  
 某公共或受保护静态字段不是常数，也不是只读字段。  
  
## 规则说明  
 不是常数也不是只读字段的静态字段不是线程安全的。  必须严格控制对这类字段的访问，并需要高级编程技术来同步对类对象的访问。  由于这些技巧难以学习和掌握，测试这类对象会带来独特挑战，因此最好使用静态字段存储不发生变化的数据。  该规则适用于库；应用程序不应公开任何字段。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将静态字段设置为常数或只读字段。  如果做不到这一点，请重新设计类型以使用替代机制，例如管理对基础字段的线程安全访问的线程安全属性。  请注意，锁争用和死锁等问题会影响库的性能和行为。  
  
## 何时禁止显示警告  
 如果您正在开发应用程序，并因此对包含静态字段的类型具有完全访问权限，则可以安全地禁止显示此规则发出的警告。  库设计者不应禁止显示此规则发出的警告；使用非常量的静态字段可能导致开发人员难以正确使用库。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]