---
title: "如何：设置分析权限 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析，设置权限"
  - "安全 [Visual Studio ALM]，设置权限"
  - "权限 [Visual Studio ALM]，分析"
  - "分析工具，设置分析权限"
  - "性能工具，设置分析权限"
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：设置分析权限
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍计算机管理员如何向在该计算机上没有管理员权限的用户或组授予进行分析所需的安全权限。  
  
 一个基本的安全原则指出，应用程序运行时不应拥有超过其所需的权限。  此原则也适用于用户。  如果当用户作为 Users 组的成员（而不是 Administrators 组的成员）登录时就具有足够的效力，则不应授予他们管理员权限。  第一个过程“创建拥有‘用户’权限的用户帐户”描述如何为 Users 组的成员创建用户帐户。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Users 组的成员将需要访问磁盘上与团队的其他成员共享的文件夹和文件。  第二个过程“授予对共享项目文件的访问权限”描述如何授予该访问权限。  
  
 如果管理员授予用户组的成员对分析工具的软件驱动程序的访问权限，则他们可以运行分析工具。  最后一个过程“授予对分析驱动程序的访问权限”描述如何授予对该驱动程序的访问权限。  
  
> [!NOTE]
>  您需要管理员权限才能执行这些过程中的步骤。  
  
### 创建拥有“用户”权限的用户帐户  
  
1.  右击**“我的电脑”**，然后单击**“管理”**。  
  
     **“计算机管理”**窗口将打开。  
  
2.  展开**“本地用户和组”**。  
  
3.  右击**“用户”**文件夹，然后单击**“新用户”**。  
  
     将出现**“新用户”**对话框。  
  
4.  将所创建的用户帐户的信息填写在此对话框的字段中。  指定一个密码。  您还可以选中要求用户下次登录时更改密码的复选框。  
  
5.  单击**“创建”**，然后单击**“关闭”**。  
  
     新用户将出现在 Users 组（一组没有“管理员”权限的用户）中。  
  
### 授予对共享项目文件的访问权限  
  
1.  在 Windows 资源管理器（或文件资源管理器）中，找到此用户使用并由项目团队共享的项目文件的文件夹树的根目录。  
  
     此文件夹的路径可能像下面这样：  
  
    ```  
    D:\ourProject  
    ```  
  
2.  右击该文件夹，然后单击**“属性”**。  
  
     将出现\<文件夹名称\>属性对话框。  
  
3.  单击**“安全”**选项卡。  
  
4.  在**“组或用户名称”**框中单击用户帐户的名称。  
  
5.  在 \<用户名\>权限 框中，选择完全控制复选框。  
  
6.  单击**“确定”**。  
  
     这将授予用户对从第 5 步所选文件夹开始的共享文件夹树的权限。  
  
### 授予对分析驱动程序的访问权限  
  
1.  作为管理员打开命令提示。  
  
2.  将目录切换到：  
  
    ```  
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
    ```  
  
3.  运行下面的命令：  
  
    ```  
    vsperfcmd /admin:driver,start /admin:service,start  
    ```  
  
     此命令将安装并启动分析工具的驱动程序。  
  
     此命令启动分析驱动程序和服务，以便非管理员用户可以使用其用户进程空间中可用的分析功能。  只有管理员才能运行此命令，非管理员用户无法运行。  
  
     请注意，除非您还执行本过程中的最后一步，否则此步骤的效果在计算机重新启动后撤消。  
  
4.  运行此命令以允许对计算机没有管理员访问权限的用户或组访问分析驱动程序功能。  
  
    ```  
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
    ```  
  
     此命令授予 \<用户名\> 或\<组名\> 帐户对分析工具的访问权限。  \<权限\> 选项决定了用户可以访问的分析功能。  \<权限\> 选项可以是下面的一个或多个值：  
  
    -   FullAccess – 允许访问所有分析方法，包括从服务、采样和跨会话分析收集性能数据。  
  
    -   SampleProfiling – 允许访问采样分析方法  
  
    -   CrossSession – 允许访问分析服务所需的跨会话分析。  
  
5.  （可选）若要在计算机重新启动以后保留以上所有步骤的效果，请运行以下命令：  
  
    ```  
    vsperfcmd /admin:driver,autostart,on  
    ```  
  
 现在，指定的用户登录后，将能够在没有管理员权限的情况下使用分析工具。  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)