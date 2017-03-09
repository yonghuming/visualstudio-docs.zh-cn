---
title: "C# 调试配置的项目设置 | Microsoft Docs"
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
  - "调试版本, 项目设置"
  - "调试配置, C#"
  - "调试配置, J#"
  - "调试 [C#], 调试器设置"
  - "调试 [J#], 调试器设置"
  - "项目配置, 调试"
  - "项目设置 [Visual Studio], 调试配置"
  - "项目 [Visual Studio], 调试配置"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C# 调试配置的项目设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可在**“属性页”**窗口中更改 C\# 调试配置的项目设置，在[调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)中对此进行了探讨。  下表显示**“属性页”**窗口中与调试器有关的设置的位置。  
  
> [!WARNING]
>  本主题不适用于 Windows 应用商店应用。  请参阅[启动调试会话（VB、C\#、C\+\+ 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> “调试”选项卡  
  
|**设置**|**描述**|  
|------------|------------|  
|**配置**|设置编译应用程序的模式。  在**“活动\(调试\)”**、**“调试”**、**“发布”**和**“所有配置”**之间进行选择。|  
|**启动操作**|这组控件指定在从“调试”菜单中选择“启动”时将发生的操作。<br /><br /> -   **“启动项目”**是默认值，用于启动启动项目以供调试。  有关更多信息，请参见[选择启动项目](http://msdn.microsoft.com/zh-cn/222e3f32-a6fe-4941-bf37-6b2a921129fd)。<br />-   **“启动外部程序”**使您可以启动和附加到不属于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目的程序。  有关更多信息，请参见[附加到正在运行的程序](http://msdn.microsoft.com/zh-cn/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)。<br />-   **“启动浏览器于 URL”**使您可以调试 Web 应用程序。|  
|**命令行参数**|指定要调试的程序的命令行参数。  该命令名是在“启动外部程序”中指定的程序名。  如果“启动操作”设置为“启动 URL”，则不能指定命令行参数。|  
|**工作目录**|指定被调试的程序的工作目录。  在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，工作目录是启动应用程序的目录，默认情况下为 \\bin\\debug。|  
|**使用远程计算机**|出于调试目的运行应用程序的远程计算机的名称或一个 [Msvsmon 服务器名称](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md)。  该 EXE 文件在远程计算机上的位置是由“配置属性”文件夹“生成”类别中的“输出路径”属性指定的。  此位置必须是远程计算机上的共享目录。|  
|**启用非托管代码调试**|使您能够从托管应用程序中调试对本机（非托管）Win32 代码的调用。|  
|**启用 SQL Server 调试**|允许对 SQL Server 数据库对象进行调试。|  
  
##  <a name="BKMK_Build_tab"></a> “生成”选项卡  
  
|设置|说明|  
|--------|--------|  
|**条件编译符号:**|此处定义 DEBUG 和 TRACE 常数。<br /><br /> 这些常数启用 [Debug 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx)和 [Trace 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx)的条件编译。  定义了这两个常数后，Debug 和 Trace 类方法将向[“输出”窗口](../ide/reference/output-window.md)生成输出。  如果没有这两个常数，则 Debug 和 Trace 类方法将不会被编译，并且不生成任何输出。<br /><br /> -   Debug 通常在程序的调试版本中定义，而不在发布版本中定义。<br />-   跟踪通常同时定义在“调试”和“发布”版本中。|  
|**优化代码**|除非发现仅出现在优化代码中的 bug，否则应在调试版本中将此设置关闭。  优化代码更难调试，因为指令与源窗口中的语句并不是直接对应的。|  
|**输出路径：**|通常设置为 bin\\Debug 以用于调试。|  
  
## 请参阅  
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)