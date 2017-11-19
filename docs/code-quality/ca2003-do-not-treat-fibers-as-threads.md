---
title: "CA2003： 不要将纤程视为线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ca9b0649950be50dcff5103258d60f6f924f12a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003：不要将纤程视为线程
|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 托管的线程被视为 Win32 线程。  
  
## <a name="rule-description"></a>规则说明  
 不要假定托管的线程是 Win32 线程。 它是纤程。 公共语言运行时 (CLR) 将作为纤程归 SQL 的实际线程的上下文中运行托管的线程。 这些线程可在 SQL Server 进程中的应用程序域和甚至数据库之间共享。 使用托管的线程本地存储区将起作用，但不是能使用非托管的线程本地存储区，也不能假定，你的代码将在当前的操作系统线程上再次运行。 不要更改设置，例如线程的区域设置。 因为它们需要进入锁的线程也必须退出锁，请勿调用 CreateCriticalSection 或通过 P/Invoke CreateMutex。 因为这将不是这种情况，当你使用纤程，Win32 临界区和互斥体将没有用处，在 SQL 中。 在托管 System.Thread 对象上，可以安全地使用大多数的状态。 这包括托管的线程本地存储区和线程的当前用户界面 (UI) 区域性。 但是，有关编程模型，因此，你将不能更改当前线程的区域性，当你使用 SQL;这将强制实施通过新的权限。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 检查你的线程的使用情况并相应地更改你的代码。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不应禁止显示此规则。