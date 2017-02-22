---
title: "“项目设计器”-&gt;“调试”页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesDebug"
helpviewer_keywords: 
  - "项目设计器，“调试”页"
  - "项目设计器中的“调试”页"
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “项目设计器”-&gt;“调试”页
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!WARNING]
>  本主题不适用于 Windows 存储 app。  参见 Windows 开发人员中心的 [启动调试会话（VB、C\#、C\+\+ 和 XAML）](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。  
  
 使用 **项目设计器** 的 **调试** 页设置调试的行为属性在 Visual Basic 或 C\#项目。  
  
 访问 **调试** 页上，选择在 **解决方案资源管理器**的项目节点。  在 **项目** 菜单中，选择 *ProjectName***属性**。  当 **项目设计器** 出现时，单击 **调试** 选项。  
  
## 配置和平台  
 以下选项允许您选择要显示或修改的配置和平台。  
  
 **配置**  
 指定要显示或修改的配置设置。  设置可以是 **调试** \(默认值\)，**发布**或 **所有配置**。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)。  
  
 **平台**  
 指定要显示或修改的平台设置。  选择可能包括 **任何 CPU**  \(默认值\)，**x64**和 **x86**。  有关更多信息，请参见[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)。  
  
## 启动操作  
 **“启动操作”**指示调试应用程序时要启动的项：项目、自定义程序、URL 或不启动任何项。  默认情况下，此选项设置为 **启动项目**。  将 **调试** 页的 **启动操作** 确定 `StartAction` 属性的值。  
  
 **启动项目**  
 选择此选项指定应启动可执行文件\(对于 Windows 应用程序和控制台应用程序项目\)，在调试应用程序时。  默认情况下此选项处于选中状态。  
  
 **启动外部程序**  
 选择此选项指定应启动特定的程序，当调试应用程序时。  
  
 **使用 URL 启动浏览器**  
 选择此选项指定应获取特定 URL，在调试应用程序时。  
  
## 启动选项  
 **命令行参数**  
 在此文本框中，输入要用于调试的命令行参数。  
  
 **工作目录**  
 在此文本框中，输入将从其中启动项目的目录。  或者单击浏览按钮\(**…** \)选择内容。  
  
 **使用远程计算机**  
 若要调试应用程序从远程计算机，请选中此复选框，然后输入路径到远程计算机上的文本框。  
  
## 启用调试器  
 **启用非托管代码调试**  
 此选项指定是否支持本机代码调试。  选择此复选框，则调用 COM 对象，或者如果启动调用您的项目，您必须调试本机代码的本机代码编写的自定义程序。  清除此复选框可禁用非托管代码调试。  默认情况下清除此复选框。  
  
 **启用 SQL Server 调试**  
 选中或清除此复选框启用或禁用 SQL 从 Visual Basic 应用程序中。  默认情况下清除此复选框。  
  
 **启用 Visual Studio 承载进程**  
 选中此复选框以启用 Visual Studio 承载进程。  默认情况下选中此复选框。  有关更多信息，请参见[承载进程 \(vshost.exe\)](../../ide/hosting-process-vshost-exe.md)。  
  
 将"安全区域"若要调试，您必须启用此选项和 **使用选定权限集调试此应用程序** 在 [“高级安全设置”对话框](../../ide/reference/advanced-security-settings-dialog-box.md)。  
  
## 请参阅  
 [使用 Visual Studio 进行调试](../../debugger/debugging-in-visual-studio.md)   
 [C\# 调试配置的项目设置](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 调试配置的项目设置](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Managing Debugging Properties](http://msdn.microsoft.com/zh-cn/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [如何：使用受限权限对 ClickOnce 应用程序进行调试](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何：创建和编辑配置](../../ide/how-to-create-and-edit-configurations.md)