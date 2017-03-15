---
title: "调试准备：ASP.NET Web 应用程序 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "调试 [Visual Studio], Web 应用程序"
  - "调试 ASP.NET Web 应用程序"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 调试准备：ASP.NET Web 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 网站模板可创建 Web 窗体应用程序。  当您使用此模板创建网站时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会创建用于调试的默认设置。  在**“项目属性”**对话框中，您可以指定是否希望该网页成为起始页。  当您以这些默认设置开始调试 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]网站时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 启动 Internet Explorer 并将调试器附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程（aspnet\_wp.exe 或 w3wp.exe）。  有关详细信息，请参阅 [系统要求](../debugger/aspnet-debugging-system-requirements.md)。  
  
### 创建 Web 窗体应用程序  
  
1.  在**“文件”**菜单上选择**“新建网站”**。  
  
2.  在**“新建网站”**对话框中，选择“[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **网站”**。  
  
3.  单击**“确定”**。  
  
### 调试 Web 窗体  
  
1.  在您的函数和事件处理程序中设置一个或多个断点。  
  
     有关详细信息，请参阅[Breakpoints and Tracepoints](http://msdn.microsoft.com/zh-cn/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
2.  命中断点时，逐句通过函数内的代码。  同时观察代码的执行，直到将问题隔离出来。  
  
     有关更多信息，请参见[Stepping](http://msdn.microsoft.com/zh-cn/8791dac9-64d1-4bb9-b59e-8d59af1833f9)和[调试 Web 应用程序和脚本](../debugger/debugging-web-applications-and-script.md)。  
  
## 更改默认配置  
 如果需要更改 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 创建的默认的调试和发布配置，则可以这样做。  有关详细信息，请参阅[如何：设置调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
#### 更改默认的调试配置  
  
1.  在**“解决方案资源管理器”**中右击网站，并选择**“属性页”**以打开**“属性页”**对话框。  
  
2.  单击**“启动选项”**。  
  
3.  将**“启动操作”**设置为应该首先显示的网页。  
  
4.  在**“调试器”**下，确保选中了**“ASP.NET 调试”**。  
  
     有关详细信息，请参阅 [Web 项目的属性页设置](../debugger/property-pages-settings-for-web-projects.md)。  
  
## 请参阅  
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)   
 [调试器基础知识](../debugger/debugger-basics.md)   
 [调试器安全](../debugger/debugger-security.md)   
 [调试托管代码](../debugger/debugging-managed-code.md)