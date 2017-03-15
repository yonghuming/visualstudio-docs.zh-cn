---
title: "错误：无法在 Web 服务器上启动调试 | Microsoft Docs"
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
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, Web 应用程序错误"
  - "调试 [Visual Studio], 错误"
  - "调试 ASP.NET Web 应用程序, 无法开始调试错误"
  - "错误 [调试器], 无法开始调试"
  - "HTTP 服务器, 调试错误"
  - "IIS, 调试 DLL"
  - "远程调试, 错误"
  - "安全性 [调试器], Web 应用程序"
  - "安全性设置, 检查默认网站"
  - "无法开始调试错误"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：无法在 Web 服务器上启动调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当你尝试调试在 Web 服务器上运行的 ASP.NET 应用程序时，可能会收到此错误消息：无法在 Web 服务器上启动调试。  
  
 在大多数情况下，发生此错误是由于未正确配置 IIS。  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> 请确保正确配置 IIS  
 有关通过 MVC 5 应用部署到 IIS 8 的信息，请参阅[发布到 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。  
  
 有关部署到 IIS7.5 的信息，请参阅[远程调试远程 IIS 7.5 计算机上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> 请确保安装了 Visual Studio 远程工具  
 如果你尝试在远程 Web 服务器上进行调试，则必须安装 Visual Studio 远程工具。 有关下载和安装远程工具的信息，请参阅[远程调试](../debugger/remote-debugging.md)。  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> 请确保已安装 ASP.NET  
 **IIS 8**  
  
 对于 IIS 8，你安装 ASP.NET 作为 IIS 的一部分。  
  
1.  在“服务器管理器”磁贴中，选择“仪表板”，然后单击“添加角色和功能”。  
  
2.  在“安装类型”页上，选择“基于角色的或基于功能的安装”，然后单击“下一步”。  
  
3.  在“选择目标服务器”页上，选择“从服务器池中选择服务器”，选择你的服务器，然后单击“下一步”。  
  
4.  在“选择服务器角色”页上，选择“Web 服务器 \(IIS\)”，然后单击“下一步”。  
  
5.  在“选择功能”页上，单击“下一步”。  
  
6.  在“Web 服务器角色 \(IIS\)”页上，单击“下一步”。  
  
7.  在“选择角色服务”页上，记下默认安装的预先选择的角色服务，依次展开“应用程序服务器”节点、“.NET Framework 4.5”节点，然后选择“ASP.NET 4.5”。 （如果你已安装 .NET 3.5，还请选择“ASP.NET 3.5”。）  
  
8.  在“确认安装选择”页上，单击“安装”。  
  
9. 在“安装进度”页上，确认你的 Web 服务器 \(IIS\) 角色和所需角色服务的安装成功完成，然后单击“关闭”。  
  
 **IIS 7.5 和更早版本**  
  
 对于 IIS 7.5 和更早版本：从命令提示符窗口中，运行以下命令：  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## 基本疑难解答  
 下面是一些你可以执行的操作以确保正确部署你的 ASP.NET 应用程序。  
  
## 在浏览器中打开 localhost 页  
 如果未正确安装 IIS，则当你在浏览器中键入 `http://localhost` 时会收到错误。  
  
## 在浏览器中打开 Web 页  
 启动 Web 浏览器，然后键入尝试调试的页的 URL（例如：`http://localhost/MyWebApplication`）。 如果 IIS 未正确配置，或未正确部署 ASP.NET 应用程序，则你会收到帮助你修复 IIS 设置以及 ASP.NET 部署的错误。  
  
## 在服务器上创建基本 ASP.NET 应用程序  
 尝试在服务器上本地创建基本 ASP.NET 应用程序并尝试对其进行调试。  
  
## 如果你使用的仅为 IP 地址，则解决验证错误  
 调试 Web 服务器要求 NTLM 身份验证。 默认情况下，IP 地址被假定为 Internet 的一部分，而在 Internet 上不进行 NTLM 身份验证。 若要更正此问题，可以指定远程计算机的名称。  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> 手动附加到进程  
 如果在开始调试时仍然收到错误消息，则可能需要尝试通过手动附加到进程来调试应用程序。  
  
-   启动应用程序而不调试。 （从**“调试”**菜单中，选择**“开始执行\(不调试\)”**。）  
  
-   单击“调试”\/“附加到进程”。  窗口出现时，启用“显示所有用户的进程”。  
  
-   找到相应的进程并附加到它。 对于 MVC 5 之前的 ASP.NET 应用，该进程是 w3wp.exe。 对于 MVC 5，请参阅[发布到 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。  
  
## 请参阅  
 [调试 Web 应用程序：错误和疑难解答](../debugger/debugging-web-applications-errors-and-troubleshooting.md)