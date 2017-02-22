---
title: "调试已部署的 Web 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET Web 应用程序"
  - "ASP.NET, 调试 Web 应用程序"
  - "调试 Web 服务"
  - "Web 服务, 调试"
  - "XML Web services, 调试"
  - "XML, 调试 Web 服务"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 调试已部署的 Web 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果需要调试正在成品服务器上运行的 Web 应用程序，则应谨慎执行此操作。  例如，如果附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程进行调试并命中了断点，辅助进程中的所有托管代码都将暂停。  暂停辅助进程中的所有托管代码会导致服务器上的所有用户的工作中断。  在成品服务器上进行调试之前，请考虑对生产工作的潜在影响。  
  
 若要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试已部署的应用程序，必须附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程，并确保调试器能够访问该应用程序的符号。  此外，还必须找到并打开该应用程序的源文件。  有关更多信息，请参见[指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)、[如何：查找 ASP.NET 进程的名称](../debugger/how-to-find-the-name-of-the-aspnet-process.md)和[系统要求](../debugger/aspnet-debugging-system-requirements.md)。  
  
> [!NOTE]
>  许多 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序都引用包含业务逻辑或其他有用代码的 DLL。  这种引用自动将 DLL 从本地计算机复制到 Web 应用程序的虚拟目录的 \\bin 文件夹中。  进行调试时，请记住 Web 应用程序引用的是 DLL 的这个副本，而不是本地计算机上的副本。  
  
 附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程与附加到任何其他远程进程的过程相同。  附加到辅助进程后，如果没有打开合适的项目，则在应用程序中断时将显示一个对话框。  此对话框将提示您提供该应用程序源文件的位置。  在该对话框中指定的文件名必须与用调试符号（位于 Web 服务器上）指定的文件名匹配。  有关详细信息，请参阅[附加到运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
## 请参阅  
 [调试 ASP.NET 和 AJAX 应用程序](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [调试 Web 应用程序和脚本](../debugger/debugging-web-applications-and-script.md)   
 [如何：为 ASP.NET 应用程序启用调试](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何：查找 ASP.NET 进程的名称](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)