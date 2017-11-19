---
title: "错误： Microsoft Visual Studio 远程调试监视器在远程计算机上以其他用户身份运行 |Microsoft 文档"
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
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f3f2c9e0b3f88734d21ae06f1af48409c58766a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>错误：远程计算机上的 Microsoft Visual Studio 远程调试监视器正以其他用户身份运行
当尝试执行远程调试时，您可能会收到如下错误信息：  
  
 远程计算机上的“Microsoft Visual Studio 远程调试监视器”正在以其他用户身份运行。  
  
## <a name="cause"></a>原因  
 当您正在“无身份验证”模式下进行调试，而启动 msvsmon 的用户不是运行 Visual Studio 的用户时，会出现此消息。  
  
## <a name="solution"></a>解决方案  
 最安全也是最好的解决方案是，以与运行 Visual Studio 的相同用户帐户运行远程调试监视器 (msvsmon.exe)。 如果无法做到这一点，你可以使用其他用户帐户下运行远程调试监视器**允许任何用户进行调试**中远程调试监视器选择选项**选项**对话框。  
  
> [!CAUTION]
>  授予其他用户进行连接的权限可能会导致意外地连接到错误的远程调试会话。 在中调试**无身份验证**模式不安全，应谨慎使用。
  
## <a name="see-also"></a>另请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)