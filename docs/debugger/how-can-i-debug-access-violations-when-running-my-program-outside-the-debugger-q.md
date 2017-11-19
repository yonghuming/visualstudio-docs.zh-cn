---
title: "在调试器外部运行程序时如何调试访问冲突？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b8a6e019725f95788b4988fbe1ddef18cb27cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>在调试器外部运行程序时如何调试访问冲突？
## <a name="problem-description"></a>问题描述  
 我的程序在 Visual Studio 环境中运行良好，但在 Windows 操作系统中独立运行时产生访问冲突。 如何调试该问题？  
  
## <a name="solution"></a>解决方案  
 设置[中实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)选项并运行独立程序，直到发生访问冲突。 然后，在**访问冲突**对话框中，你可以单击**取消**以启动调试器。  
  
 请参见知识库文章 Q133174“How to Locate Where a General Protection (GP) Fault Occurs”（如何定位通用性保护 (GP) 错误的发生位置）。 你可以找到知识库文章位于 MSDN 库 CD 上还是通过搜索[http://support.microsoft.com/](http://support.microsoft.com/)。  
  
## <a name="see-also"></a>另请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [调试本机代码](../debugger/debugging-native-code.md)