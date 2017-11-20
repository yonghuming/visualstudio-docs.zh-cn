---
title: "尝试联系远程计算机 DCOM 错误时发生。 拒绝访问。 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe153a5252603cf967b396932a6479a8df437a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>尝试联系远程计算机 DCOM 错误时发生。 拒绝访问。
远程调试使用 DCOM 在以下情况下进行本地和远程计算机之间的通信：  
  
-   调试器设置为**本机兼容模式**或**托管兼容模式**签入**工具 > 选项 > 调试**页  
  
-   调试的是托管 C++ (C++/CLI) 代码。  
  
-   在 Visual Studio 2013 中，当**启用本机编辑并继续**签入**工具 > 选项 > 调试**页  
  
-   某些第三方调试方案  
  
 当 Visual Studio 进程无法通过 DCOM 针对远程调试器进程验证自己的身份（或提供的凭据被视为不足）时，将出现此错误。 以下一个或多个解决方法可解决此问题：  
  
-   关闭“本机兼容模式”   和“托管兼容模式” 。  
  
-   在 Visual Studio 2013 中，关闭“启用本机编辑并继续” 。  
  
-   重新启动这两台计算机。  
  
-   如果远程调试要求输入凭据，则选中该选项以保存凭据。  
  
## <a name="see-also"></a>另请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)