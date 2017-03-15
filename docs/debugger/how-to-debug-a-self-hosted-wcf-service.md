---
title: "如何：调试自我托管的 WCF 服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "调试, WCF"
  - "WCF, 调试"
  - "WCF, 自我承载的服务"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：调试自我托管的 WCF 服务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“自我托管服务”是指不在 IIS、WCF 服务主机或 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 开发服务器内部运行的 WCF 服务。  若要调试自我托管的 WCF，最简便的方法是配置 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，以使其在您选择**“调试”**菜单上的**“启动调试”**时启动客户端和服务器。  
  
 如果 WCF 服务承载在自己内部，或者是无法以此方式启动的进程（例如 NT 服务），则不能使用此方法。  此时，可改为执行下列操作之一：  
  
-   手动将调试器附加到承载进程。  有关详细信息，请参阅[附加到运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
     \- 或 \-  
  
-   开始调试客户端，然后单步执行对服务的调用。  这需要在 app.config 文件中启用调试。  有关更多信息，请参见[WCF 调试的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### 从 Visual Studio 中同时启动客户端和宿主  
  
1.  创建一个同时包含客户端和服务器项目的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案。  
  
2.  配置该解决方案，以使其在您选择**“调试”**菜单上的**“启动”**时启动客户端和服务器进程。  
  
    1.  在**“解决方案资源管理器”**中右击该解决方案的名称。  
  
    2.  单击**“设置启动项目”**。  
  
    3.  在**解决\<名称\>属性**对话框；选择**多启动项目**。  
  
    4.  在**“多启动项目”**网格中，在与服务器项目对应的行上单击**“操作”**，然后选择**“启动”**。  
  
    5.  在与客户端项目对应的行上，单击**“操作”**，然后选择**“启动”**。  
  
    6.  单击“确定”。  
  
## 请参阅  
 [调试 WCF 服务](../debugger/debugging-wcf-services.md)   
 [WCF 调试的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：单步执行 WCF 服务](../debugger/how-to-step-into-wcf-services.md)