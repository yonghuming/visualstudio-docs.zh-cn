---
title: "如何： 查找 ASP.NET 进程的名称 |Microsoft 文档"
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03ae4956f0e16a4fb9267266ebc6b6c335c95eac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>如何：查找 ASP.NET 进程的名称
若要附加到正在运行的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序，您必须知道 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 进程的名称：  

-   如果你在 IIS 或 IISExpress 上运行 ASP.NET 核心，进程名称是 dotnet.exe。

-   如果你运行 ASP.NET IIS 6.0 上更高版本，则名称为 w3wp.exe。  
  
-   如果你在早期版本的 IIS 上运行 ASP.NET，名称为 aspnet_wp.exe。

-   如果你正在 IISExpress 上运行 ASP.NET，名称为 iisexpress.exe。
  
通过使用 Visual Studio 2012 之前的 Visual Studio 的版本生成的应用程序[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]代码可能驻留在文件系统，并在测试服务器 WebDev.WebServer.exe 或 WebDev.WebServer40.exe 下运行。 在这种情况下，必须将附加到 WebDev.WebServer.exe 或而不是 WebDev.WebServer40.exe[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]过程。 此方案仅适用于本地调试。
  
当原来的 ASP 应用程序在进程内运行时，它们会在 IIS 进程 inetinfo.exe 内部运行。  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>确定应用程序正在哪个 IIS 版本下运行  

1.  请确保应用程序正在运行，然后，从 Visual Studio 中，使用[附加到进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)命令。

2.  键入类似 w3wp.exe 以进行快速查找中的进程的进程名称的首字母**可用进程**列表。

    本主题中的列表中的可用进程将指示的 IIS 的版本可用，以及哪个进程正在运行你的应用程序。

    > [!NOTE]
    > 从 Visual Studio 2017 年 1 开始，你可以使用搜索框中搜索进程名称。
  
## <a name="see-also"></a>另请参阅  
 [附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [远程调试 Web 应用程序的必备组件](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [系统要求](../debugger/aspnet-debugging-system-requirements.md)   
 [调试 ASP.NET 应用程序](../debugger/how-to-enable-debugging-for-aspnet-applications.md)