---
title: "管理-并行文件关联 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "设置默认的谓词"
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 管理-并行文件关联
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果 VSPackage 提供文件关联，您必须如何确定到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的特定版本应调用打开文件的处理并行安装。  不兼容的文件格式配制问题。  
  
 用户希望产品的新版本与早期版本兼容，因此，现有文件较新版本可加载，而不会丢失数据。  理想情况下， VSPackage 中加载和保存早期版本文件格式。  如果不为 true，则应该提供升级文件格式转换为 VSPackage 的新版本。  弊端是升级的文件处于较早版本不能打开。  
  
 文件时，在窗体变得不兼容时，若要避免此问题，您可以更改扩展。  例如， VSPackage 的 1 版可以使用此扩展， .mypkg10，并且，版本 2 可以使用此扩展， .mypkg20。  此差异标识打开特定文件的 VSPackage。  如果添加较新的 Vspackage 到与早期扩展程序的列表，用户可以右击文件并选择以打开它在较新的 VSPackage。  此时， VSPackage 中提供文件升级到新的布局或打开文件并保持与 VSPackage 的早期版本兼容。  
  
> [!NOTE]
>  可以将这些方法。  例如，您可以通过加载较旧的文件提供向后兼容和提供升级文件格式，当用户保存它。  
  
## 面对问题  
 如果需要多个并行的 Vspackage 使用同一个扩展，您必须选择与该扩展 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的版本。  这是两个选择:  
  
-   打开在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 最新版本的文件安装在用户的计算机。  
  
     此方法，安装程序来确定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的最新版本以及包含该负责在为文件关联编写的注册表项。  在 Windows Installer 包，可以包括自定义操作设置一 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的最新版本的属性。  
  
    > [!NOTE]
    >  在此上下文中， “最新的”表示 “最新版本”。这些安装程序项将不会自动检测 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]后续版本。  项。 [检测系统要求](../extensibility/internals/detecting-system-requirements.md) 和在 [必须在安装后运行的命令](../extensibility/internals/commands-that-must-be-run-after-installation.md) 类似于存在的一个此处以及需要支持 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的其他版本。  
  
     在 CustomAction 的以下行表设置 DEVENV\_EXE\_LATEST 属性是 AppSearch 和 RegLocator 表设置的属性讨论在 [必须在安装后运行的命令](../extensibility/internals/commands-that-must-be-run-after-installation.md)。  行。 InstallExecuteSequence 表中计划自定义操作的早期执行顺序。  在这种情况列的值提交逻辑工作:  
  
    -   ，如果它是唯一的当前版本， Visual Studio .NET 2002 中是最新的版本。  
  
    -   Visual Studio .NET 2003 中是最新版本，仅当存在，并且 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不存在。  
  
    -   ，如果它是唯一的当前版本，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 是最新的版本。  
  
     这种实际结果是 DEVENV\_EXE\_LATEST 包含 devenv.exe 的最新版本的路径。  
  
    ### CustomAction 确定 Visual Studio 的最新版本的表行  
  
    |操作|类型|源|Target|  
    |--------|--------|-------|------------|  
    |CA\_SetDevenvLatest\_2002|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2002\]|  
    |CA\_SetDevenvLatest\_2003|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2003\]|  
    |CA\_SetDevenvLatest\_2005|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2005\]|  
  
    ### InstallExecuteSequence 确定 Visual Studio 的最新版本的表行  
  
    |操作|Condition|顺序|  
    |--------|---------------|--------|  
    |CA\_SetDevenvLatest\_2002|DEVENV\_EXE\_2002 和非 \(DEVENV\_EXE\_2003 或 DEVENV\_EXE\_2005\)|410|  
    |CA\_SetDevenvLatest\_2003|而不是 DEVENV\_EXE\_2003 DEVENV\_EXE\_2005|420|  
    |CA\_SetDevenvLatest\_2005|DEVENV\_EXE\_2005|430|  
  
     您在 Windows Installer 包的注册表表中使用 DEVENV\_EXE\_LATEST 属性编写 HKEY\_CLASSES\_ROOT \\*ProgId*\\Shell\\Open\\Command key's default value， \[DEVENV\_EXE\_LATEST\] “%1 "  
  
-   运行可能由可用 VSPackage 版本做出最好的选择的共享启动器程序。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 开发人员选择此方法处理解决方案多种格式的复杂要求和项目从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的许多版本的该结果。  此方法，您注册启动器程序作为扩展处理程序。  启动签出文件确定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的版本和 VSPackage 可以特定文档的事件。  例如，因此，如果用户打开由 VSPackage 的特定版本上次保存的文件，启动器开始在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]匹配版本的该 VSPackage。  此外，用户可以配置启动器始终启动最新的版本。  启动器还可以提示用户升级文件的格式。  如果文件的格式包括一个版本号，启动器会通知用户，如果文件格式是从与一个或多个后安装的 Vspackage 的版本。  
  
     启动器应在使用 VSPackage 的所有版本共享的 Windows Installer 组件。  此过程确保始终安装最新版本和不会移除，直到 VSPackage 的所有版本中卸载。  这样，文件关联和启动组件的其他注册表项保留，即使 VSPackage 的一个版本中卸载。  
  
## 卸载和文件关联  
 卸载 VSPackage 写入文件关联的注册表项移除文件关联。  因此，该扩展没有关联的程序。  Windows Installer “无法恢复”添加的注册表项，当安装 VSPackage。  这是一些可以修复用户文件关联:  
  
-   如使用共享启动器元素。  
  
-   提示用户运行 VSPackage 版本的修复用户希望拥有文件关联。  
  
-   提供复盖相应的注册表项的单独的可执行程序。  
  
-   提供配置选项让用户选择文件关联和还原失去的关联页或对话框。  提示用户在其卸载。  
  
## 请参阅  
 [注册由并行部署的文件扩展名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [注册文件扩展名的谓词](../extensibility/registering-verbs-for-file-name-extensions.md)