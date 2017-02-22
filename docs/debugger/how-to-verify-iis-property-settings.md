---
title: "如何：验证 IIS 属性设置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "调试 Web 应用程序, 疑难解答"
  - "IIS 管理工具"
  - "IIS, 属性设置"
  - "属性 [调试器], 用 IIS 管理工具设置"
  - "Web 应用程序, 设置属性"
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：验证 IIS 属性设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 IIS 管理工具，可以设置 Web 应用程序的属性。  这些属性必须正确设置，应用程序才能运行，所以，验证这些设置通常是疑难解答的必需步骤。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 检查 Web 应用程序的 IIS 设置  
  
1.  打开**“管理工具”**窗口：在**“开始”**菜单中，指向**“程序”**，再选择**“管理工具”**。  如果**“程序”**菜单中没有**“管理工具”**，则在**“控制面板”**中查找它。  
  
    -   在 Windows 2000 中，选择**“Internet 服务管理器”**。  
  
    -   在 Windows XP 中，选择**“Internet 信息服务”**。  
  
    -   在 Windows Server 2003 中，双击**“管理您的服务器”**。  
  
         将打开**“管理您的服务器”**窗口。  在**“应用程序服务器”**下面，单击**“管理此应用程序服务器”**。  
  
         将打开**“应用程序服务器”**窗口。  在左侧窗格中，打开**“Internet 信息服务 \(IIS\) 管理器”**节点。  
  
2.  在该对话框中，单击表示您的计算机的树控件节点。  单击**“网站”**节点，再选择该 Web 应用程序的节点。  该节点可以是网站节点（因而是**“默认网站”**节点的同级节点），也可以是现有网站节点下面的虚拟目录节点。  
  
3.  右击该 Web 应用程序，然后在快捷菜单上，单击**“属性”**。  
  
4.  验证该 Web 应用程序的安全设置。  
  
    1.  在 Web 应用程序的**“属性”**窗口中，单击**“目录安全性”**选项卡，再单击**“编辑”**。  
  
    2.  在**“身份验证方法”**对话框中，如果尚未选择**“启用匿名访问”**和**“集成的 Windows 身份验证”**，则选择它们。  
  
    3.  单击**“确定”**关闭**“身份验证方法”**对话框。  
  
5.  对于 ATL Server 应用程序，请验证 DEBUG 谓词是否与您的 ISAPI 扩展相关联。  有关详细信息，请参阅[How to: Associate DEBUG Verb with Extension](http://msdn.microsoft.com/zh-cn/50d261d3-4bd4-41c0-b44e-3591086f121e)。  
  
6.  对于 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序，请确保应用程序的虚拟文件夹中具有在**“Internet 信息服务\(IIS\)管理器”**、**“Internet 服务管理器”**或**“Internet 信息服务”**中设置的应用程序名称。  
  
    1.  在 Web 应用程序的**“属性”**窗口中，选择**“目录”**选项卡（如果该应用程序位于虚拟目录中），或选择**“主目录”**选项卡（如果该应用程序位于网站中）。  
  
    2.  验证**“本地路径”**中的名称与应用程序实际部署到的目录的名称是否匹配。  
  
    3.  在**“应用程序设置”**下，键入包含应用程序的根目录的名称。  
  
    4.  单击**“确定”**关闭**“属性”**对话框。  
  
7.  对于 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序，请单击 **ASP.NET** 选项卡，并验证是否指定了正确的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 版本。  
  
8.  单击**“确定”**关闭**“属性”**对话框。  
  
9. 单击**“确定”**关闭**“Internet 信息服务\(IIS\)管理器”**、**“Internet 服务管理器”**或**“Internet 信息服务”**对话框。  
  
## 请参阅  
 [疑难解答](../debugger/debugging-web-applications-troubleshooting.md)