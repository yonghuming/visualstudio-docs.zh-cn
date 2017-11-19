---
title: "异常后继续执行 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9491eb19796c766d216af458ca122b1fa5032596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="continuing-execution-after-an-exception"></a>在出现异常之后继续执行
当调试器因异常而中断执行时，你将看到**异常帮助器**，默认情况下。 如果你已禁用**异常帮助器**中**选项**对话框中，你将看到**异常助手**（C# 或 Visual Basic） 或**异常**对话框 （c + +）。  
  
 当**异常帮助器**出现时，你可以尝试修复导致异常的问题。
  
## <a name="managed-and-native-code"></a>托管和本机代码  
 在托管和本机代码中，你可以在发生未经处理的异常后在同一线程内继续执行。 **异常帮助器**展开到点引发异常的调用堆栈。
  
## <a name="mixed-code"></a>混合代码  
 如果在调试本机和托管混合的代码时遇到未经处理的异常，则操作系统约束将阻止调用堆栈展开。 如果尝试使用快捷菜单来展开调用堆栈，则会出现一个错误消息，告诉你在混合代码调试期间，调试器无法在异常未得到处理的情况下展开调用堆栈。  
  
## <a name="see-also"></a>另请参阅  
 [管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)