---
title: "错误：调试失败，因为没有启用集成 Windows 身份验证 | Microsoft Docs"
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
  - "vs.debug.error.webdbg_ntlm_authn_not_enabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "调试器, Web 应用程序错误"
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：调试失败，因为没有启用集成 Windows 身份验证
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

由于身份验证错误，无法对请求调试的用户进行身份验证。  当您尝试单步执行 Web 应用程序或 XML Web services 时，就可能出现此问题。  导致此错误的一种原因是没有启用集成 Windows 身份验证。  若要启用该身份验证，请按照“启用集成 Windows 身份验证”中的步骤操作。  
  
 如果已启用集成 Windows 身份验证，但仍然出现此错误，则导致此错误的原因可能是启用了**“Windows 域服务器的摘要式身份验证”**。  在这种情况下，应与您的网络管理员联系。  
  
### 启用集成 Windows 身份验证  
  
1.  使用管理员帐户登录 Web 服务器。  
  
2.  单击**“开始”**，再单击**“控制面板”**。  
  
3.  在**“控制面板”**中双击**“管理工具”**。  
  
4.  双击**“Internet 信息服务”**。  
  
5.  单击 Web 服务器节点。  
  
     服务器名称下方将打开一个**“网站”**文件夹。  
  
6.  您可以为所有网站或个别网站配置身份验证。  若要为所有网站配置身份验证，请右击**“网站”**文件夹，然后单击**“属性”**。  若要为单个网站配置身份验证，请打开**“网站”**文件夹，右击单个网站，然后单击**“属性”**。  
  
     屏幕上会显示**“属性”**对话框。  
  
7.  单击**“目录安全性”**选项卡。  
  
8.  在**“匿名访问和身份验证控制”**节中，单击**“编辑”**。  
  
     将显示**“身份验证方法”**对话框。  
  
9. 在**“用户访问需经过身份验证”**下，选择**“集成 Windows 身份验证”**。  
  
10. 单击**“确定”**关闭**“身份验证方法”**对话框。  
  
11. 单击**“确定”**关闭**“属性”**对话框。  
  
12. 关闭**“Internet 信息服务”**窗口。  
  
### 在 Windows Vista\/IIS 7 中启用集成 Windows 身份验证  
  
1.  使用管理员帐户登录 Web 服务器。  
  
2.  按照下列步骤启用 Windows 身份验证和 II6 管理兼容性（如果尚未启用）：  
  
    1.  依次单击**“开始”**、**“控制面板”**、**“程序”**。  
  
    2.  在**“程序和功能”**下单击**“打开或关闭 Windows 功能”**。  
  
         将出现“用户帐户控制”对话框，并提示您是否允许继续。  
  
    3.  单击**“继续”**。  
  
         将出现“Windows 功能”对话框。  
  
    4.  在功能列表中，展开**“Internet 信息服务”**节点。  
  
    5.  在**“Internet 信息服务”**下，展开**“万维网服务”**节点。  
  
    6.  在**“万维网服务”**下，单击**“安全”**。  
  
    7.  单击**“Windows 身份验证”**。  
  
    8.  在**“Internet 信息服务”**下，展开**“Web 管理工具”**节点。  
  
    9. 在**“Web 管理工具”**下，展开**“IIS 6 管理兼容性”**节点，然后选中**“IIS 6 元数据库和 IIS 6 配置兼容性”**复选框。  
  
    10. 在**“Web 管理工具”**下，选择**“IIS 管理控制台”**，然后单击**“确定”**。  
  
    11. 重新启动计算机，以使这些更改生效。  
  
3.  单击**“开始”**，然后单击**“控制面板”**。  
  
4.  单击**“经典视图”**，然后双击**“管理工具”**。  
  
5.  在**“名称”**列中，双击**“Internet 信息服务\(IIS\)管理器”**。  
  
6.  在**“连接”**列中，展开您的服务器节点。  
  
     服务器名称下方将打开一个**“网站”**文件夹。  
  
7.  展开**“网站”**节点，然后单击要为其启用集成 Windows 身份验证的网站。  
  
8.  中心窗格标题将更改为所选网站的名称。  在此窗格的**“IIS”**标题下，双击**“身份验证”**。  
  
     该窗格的标题将更改为**“身份验证”**。  
  
9. 在**“身份验证”**窗格的**“名称”**列中，右击**“Windows 身份验证”**，然后单击**“启用”**。  
  
10. 关闭**“Internet 信息服务\(IIS\)管理器”**窗口。  
  
## 请参阅  
 [调试 Web 应用程序：错误和疑难解答](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft 摘要式身份验证](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Running Web Applications on Windows Vista with IIS 7.0 and Visual Studio](../Topic/Running%20Web%20Applications%20on%20Windows%20Vista%20with%20IIS%207.0%20and%20Visual%20Studio.md)