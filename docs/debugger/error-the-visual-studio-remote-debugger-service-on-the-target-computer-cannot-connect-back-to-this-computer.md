---
title: "错误: 目标计算机上的 Visual Studio 远程调试器服务无法重新连接到此计算机 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.service_access_denied_oncallback"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误: 目标计算机上的 Visual Studio 远程调试器服务无法重新连接到此计算机
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此错误表示“Visual Studio 远程调试器”服务正在运行，但是运行它的用户帐户在连接到正在从中进行调试的计算机时无法进行身份验证。  
  
 下表显示可访问该计算机的帐户：  
  
|||||  
|-|-|-|-|  
||LocalSystem 帐户|域帐户|在双方计算机上具有相同用户名和密码的本地帐户|  
|双方计算机处于同一个域中|是|是|是|  
|双方计算机处于具有双向信任的域中|否|否|是|  
|双方计算机中有一台或两台都处于工作组中|否|否|是|  
|不同域中的计算机|否|否|是|  
  
 此外：  
  
-   运行“Visual Studio 远程调试器”服务的帐户应为远程计算机上的管理员，这样它就能调试任何进程。  
  
-   还必须授予该帐户在使用**“本地安全策略”**管理工具的远程计算机上 `Log on as a service` 的特权。  
  
-   如果正使用本地帐户访问计算机，则必须在本地帐户下运行“Visual Studio 远程调试器”服务。  
  
### 更正此错误  
  
1.  确保在远程计算机上正确设置“Visual Studio 远程调试器”服务。  有关详细信息，请参阅[在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。  
  
2.  以可以访问调试器主机的帐户运行远程调试器服务，如上表所示。  
  
### 添加“作为服务登录”特权  
  
1.  在**“开始”**菜单上选择**“控制面板”**。  
  
2.  如有必要，在控制面板中选择**“经典视图”**。  
  
3.  双击**“管理工具”**。  
  
4.  在“管理工具”窗口中双击**“本地安全策略”**。  
  
5.  在**“本地安全设置”**窗口中展开**“本地策略”**文件夹。  
  
6.  单击**“用户权限分配”**。  
  
7.  在**“策略”**列中，双击**“作为服务登录”**，在**“作为服务登录”**对话框中查看当前的本地组策略分配。  
  
8.  若要添加新用户，请单击**“添加用户或组”**按钮。  
  
9. 完成添加用户后，单击**“确定”**。  
  
### 解决此错误  
  
-   将“远程调试监视器”作为应用程序（而不是作为服务）运行。  
  
## 请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)