---
title: "错误： 评估函数 &#39; 函数 &#39;操作已超时，需以不安全的方式中止 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 722abd91cb9f97aab67d0d9a5e77ff9e3a4f080d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>错误： 评估函数 &#39; 函数 &#39;操作已超时，需以不安全的方式中止

完整消息文本： 函数 function 求值超时，并且需要以不安全的方式将中止。 这可能会损坏目标进程。 

若要更加轻松地检查.NET 对象的状态，调试器将自动强制执行调试的进程来运行其他代码 （通常是属性 getter 方法和 ToString 函数）。 在大多数的所有情况下，这些函数快速完成，并让调试更加容易。 但是，调试器不能在沙盒中运行应用程序。 因此，属性 getter 或调入挂起的本机函数的 ToString 方法可能导致长的超时可能无法恢复的。 如果遇到此错误消息，你将会发生这种情况。
 
此问题的一个常见原因是当调试器将计算属性，则它仅允许正在检查要执行的线程。 因此如果属性正在等待其他线程运行在调试应用程序，并且如果它正在等待.NET 运行时无法中断的方式，将出现此问题。
 
## <a name="to-correct-this-error"></a>更正此错误
 
有三个可能的解决方案，此问题。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解决方案 #1： 防止调试器调用属性 getter 或 ToString 方法
 
错误消息将通知调试器尝试调用该函数的名称。 如果可以修改此函数，则你可以调用属性 getter 或 ToString 方法阻止调试器。 请尝试以下方法之一：
 
* 将方法更改为某些其他类型的属性 getter 除了代码或 ToString 方法和问题将会消失。
    - 或 -
* （对于 ToString)在类型上定义 DebuggerDisplay 特性，可以让调试器评估 ToString 之外的内容。
    - 或 -
* （适用于属性 getter)Put`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`的属性上的属性。 这很有用，如果你的需要的属性的 API 兼容性原因，一个方法，但它确实应该为一种方法。
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>解决方案 2： 具有目标代码要求调试器中止评估
 
错误消息将通知调试器尝试调用该函数的名称。 如果属性 getter 或 ToString 方法有时会失败。 要正确运行，尤其是在其中问题在于的情况下的代码需要另一个线程来运行代码，然后实现函数可以调用`System.Diagnostics.Debugger.NotifyOfCrossThreadDependency`提出调试器 abort 函数评估。 使用此解决方案中，仍可以显式评估了这些函数中，但默认行为是执行停止 NotifyOfCrossThreadDependency 调用发生时。
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>解决方案 #3： 禁用所有隐式计算
 
如果以前的解决方案不解决此问题，请转到*工具* > *选项*，并取消选中设置*调试* >  *常规* > *启用属性求值和其他隐式函数调用*。 这将禁用大多数隐式函数计算，并应该解决此问题。



  
