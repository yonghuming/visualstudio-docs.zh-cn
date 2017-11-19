---
title: "调试和承载进程 |Microsoft 文档"
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
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cdf8b50415a238c2af2735a20fea4ed8c23668
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-and-the-hosting-process"></a>调试和承载进程
Visual Studio 宿主进程提高了调试器性能，并启用了新的调试器功能，如部分信任调试和设计时表达式计算。 如果需要，你可以禁用宿主进程。 有关详细信息，请参阅 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md)。 以下部分描述用宿主进程和不用宿主进程进行调试的一些差异。  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>部分信任调试和 Click-Once 安全  
 部分信任调试需要宿主进程。 如果禁用宿主进程，部分信任调试将不工作，即使在 **“项目属性”** 的 **“安全”**页上启用了部分信任安全。 有关详细信息，请参阅 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) 和 [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md)。  
  
## <a name="design-time-expression-evaluation"></a>设计时表达式计算  
 设计时表达式始终使用宿主进程。 如果在 **“项目属性”** 中禁用宿主进程，则禁用了类库项目的设计时表达式计算。 对于其他项目类型，不禁用设计时表达式计算。 相反，Visual Studio 启动实际可执行文件，并将它用于不用宿主进程的设计时计算。 这种差异可能产生不同的结果。  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName 差异  
 `AppDomain.CurrentDomain.FriendlyName` 依据是否启用宿主进程返回不同的结果。 如果在启用宿主进程时调用 `AppDomain.CurrentDomain.FriendlyName` ，它将返回 *app_name*`.vhost.exe`。 如果在启用宿主进程时调用它，它将返回 *app_name*`.exe`。  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName 差异  
 `Assembly.GetCallingAssembly().FullName` 依据是否启用宿主进程返回不同的结果。 如果在启用宿主进程时调用 `Assembly.GetCallingAssembly().FullName` ，它将返回 `mscorlib`。 如果禁用宿主进程时调用 `Assembly.GetCallingAssembly().FullName` ，它将返回该应用程序名。  
  
## <a name="see-also"></a>另请参阅  
 [承载进程 (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [如何： 调试部分信任应用程序](../debugger/how-to-debug-a-partial-trust-application.md)   
 [如何：禁用承载进程](../ide/how-to-disable-the-hosting-process.md)