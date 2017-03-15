---
title: "远程调试远程 IIS 7.5 计算机上的 ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 远程调试远程 IIS 7.5 计算机上的 ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

你可以将 ASP.NET Web 应用程序部署到具有 IIS 7.5 的 Windows Server 2008 R2 计算机，并将其设置为远程调试。 下面的说明解释如何设置和配置一个 Visual Studio 2015 MVC 4.5.2 应用程序。  
  
## 在 Visual Studio 计算机上创建该应用程序  
  
1.  创建新的 MVC ASP.NET 应用程序。 （“文件”\/“新建”\/“项目”，然后选择“Visual C\#”\/“Web”\/“ASP.NET Web 应用程序”。 在 **ASP.NET 4.5.2** 模板部分中，选择“MVC”。 取消“配置 Microsoft Azure Web App”页。 ）并将其命名为 **MyMVC**。  
  
2.  打开 HomeController.cs 文件，并在 `About()` 方法中设置断点。  
  
3.  在“解决方案资源管理器”中，右键单击项目节点并选择“发布”。  
  
4.  对于“选择发布目标”，选择“自定义”并将该配置文件的命名 **MyMVC**。 单击“下一步”。  
  
5.  在“连接”选项卡上，将“发布方法”字段设置为“文件系统”，并将“目标位置”字段设置为一个本地目录。 单击“下一步”。  
  
6.  设置配置为“调试”。 单击“发布”。  
  
     应将该应用程序发布到本地目录。  
  
## 部署 Windows Server 远程计算机上的应用程序  
 本节假定 Windows Server 2008 R2 计算机已经启用了 IIS。  
  
1.  安装 ASP.NET：  
  
     **C:\\Windows\\Microsoft.NET\\Framework \(64\) \\v4.0.30319\\aspnet\_regiis.exe ir**  
  
2.  将 ASP.NET 项目目录从 Visual Studio 计算机复制到 Windows Server 计算机上的本地目录（我们命名为 **C:\\Publish**）。  
  
3.  请确保 web.config 文件列出了.NET Framework 的正确版本。  默认情况下，在此计算机上安装的.NET Framework 版本是 4.0.30319，但我们创建了一个 ASP.NET 4.5.2 版本。 如果在 Windows Server 计算机上未安装此版本，你需要更改版本：  
  
    ```xml  
    <system.web> <authentication mode="None" /> <compilation debug="true" targetFramework="4.0.30319" /> <httpRuntime targetFramework="4.0.30319" /> </system.web>  
  
    ```  
  
4.  打开“Internet 信息服务\(IIS\)管理器”并转到“站点”。  
  
5.  右键单击“默认网站”节点，然后选择“添加应用程序”。  
  
6.  将“别名”字段设置为 **MyMVC**并将应用程序池字段设置为 **ASP.NET v4.0**。 将“物理路径”设置为 **C:\\Publish**（复制 ASP.NET 项目目录的位置）。  
  
7.  若要测试部署，请右键单击“默认网站”，并选择“浏览”。 将显示网页。  
  
## 在 Windows Server 计算机上安装远程调试器  
 有关如何下载远程调试器的说明，请参阅[远程调试](../debugger/remote-debugging.md)。  
  
 若要执行的 ASP.NET 应用程序的远程调试，可以启动远程调试器作为服务，或以管理员身份运行远程调试器应用程序。 有关如何运行作为一项服务的远程调试器的详细信息，请参阅[远程调试](../debugger/remote-debugging.md)。  
  
## 从 Visual Studio 计算机附加到 ASP.NET 应用程序  
  
-   在 Visual Studio 计算机上打开 **MyMVC** 解决方案。  
  
-   在 Visual Studio 中，单击“调试”\/“附加到进程”。  
  
-   将限定符字段设置为 **\<remote computer name\>:4020**。  
  
-   “可用进程”窗口中将显示某些进程。  
  
-   勾选“显示所有用户的进程”。  
  
-   查找 **w3wp.exe** 并单击“附加”。  
  
-   打开远程计算机的网站。 在浏览器中，转到 **http:\/\/\<remote computer name\>**。  
  
-   将显示 ASP.NET 网页。 单击“关于”。  
  
     应在 Visual Studio 中命中断点。