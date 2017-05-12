---
title: "如何：安装 Visual Studio Tools for Office Runtime 可再发行组件"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "在 Visual Studio 中安装 Office 开发工具"
  - "Office 运行时 [Visual Studio 中的 Office 开发]"
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: 94
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 93
---
# 如何：安装 Visual Studio Tools for Office Runtime 可再发行组件
  在运行使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 Microsoft Office 开发人员工具创建的解决方案的每台计算机上，必须安装 Visual Studio 2010 Tools for Office Runtime。  安装 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 Microsoft Office 时会自动安装运行时。  有关详细信息，请参阅 [Visual Studio Tools for Office Runtime 安装方案](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)。  
  
 在以下情况，你可能需要按照手动安装说明操作：  
  
-   需要在服务器上安装 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  例如，希望使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类来管理服务器上的文档级解决方案。  
  
-   需要在已安装 Office 解决方案的所有其他先决条件的计算机上安装运行时。  
  
    > [!NOTE]  
    >  若要安装 .NET Framework 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，你必须是开发计算机上的管理员。  
  
### 安装 Visual Studio Tools for Office runtime  
  
1.  安装 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本。  
  
    -   若要下载 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]，请参阅 [Microsoft.NET Framework 4（Web 安装程序）](http://go.microsoft.com/fwlink/?LinkId=178957)。  
  
    -   若要下载 [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]，请参阅 [Microsoft.NET Framework 4 Client Profile（Web 安装程序）](http://go.microsoft.com/fwlink/?LinkId=178958)。  
  
    -   若要下载 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，请参阅 [Microsoft.NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)。  
  
2.  运行 vstor\_redist.exe 以安装 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
     可从 [Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384) 下载这些安装文件。  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的先决条件与 .NET Framework 的先决条件相匹配。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 包括语言包。  如果 Windows 安装设置为非英语语言，则可以以 Windows 使用的语言显示运行时消息。  同样，如果最终用户安装 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，然后在设置为非英语语言的 Windows 安装上运行你的解决方案，则运行时消息将以与 Windows 相同的语言显示。  在某些情况下，可能需要其他语言包。  例如，如果你的 Windows 副本使用多个语言设置，或在安装 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 后切换到另一种语言，则可能需要其他语言包。  可从[Microsoft Visual Studio 2010 Tools for Microsoft Office System（4.0 版运行时）语言包](http://go.microsoft.com/fwlink/?LinkId=140386)下载语言包 。  
  
## 请参阅  
 [入门（Visual Studio 中的 Office 开发）](../vsto/getting-started-office-development-in-visual-studio.md)   
 [将计算机配置为开发 Office 解决方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [如何：将计算机配置为开发 Office 解决方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [如何：安装 Office 主互操作程序集](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  