---
title: "CA2003：不要将纤程视为线程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2003：不要将纤程视为线程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大更改|  
  
## 原因  
 托管线程被视为 Win32 线程。  
  
## 规则说明  
 不要假定托管线程是 Win32 线程。  它是纤程。  公共语言运行时库 \(CLR\) 将在 SQL 所拥有的真正线程的上下文中作为纤程运行托管的线程。  这些线程可以在 AppDomain 之间甚至 SQL Server 进程中的数据库之间共享。  可以使用托管线程本地存储区，但不能使用非托管线程本地存储区，也不能假定代码将再次运行在当前操作系统线程上。  不要更改线程的区域设置等设置。  不要通过 P\/Invoke 调用 CreateCriticalSection 或 CreateMutex，因为它们需要能够进入锁也必须退出锁的线程。  由于使用纤程不会出现上述问题，因此 Win32 临界区和 mutex 在 SQL 中毫无用处。  可以在托管的 System.Thread 对象上安全地使用大部分状态。  这包括托管的线程本地存储区和线程的当前用户界面 \(UI\) 区域性。  但由于要使用编程模型，因此在使用 SQL 时将不能更改线程的当前区域性；这一点将通过新的权限来强制实现。  
  
## 如何解决冲突  
 检查线程的使用情况并对代码进行相应的更改。  
  
## 何时禁止显示警告  
 不应禁止显示此规则。