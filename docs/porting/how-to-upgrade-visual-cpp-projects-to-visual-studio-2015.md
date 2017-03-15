---
title: "如何：将 Visual C++ 项目升级到 Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [C++], 升级"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将 Visual C++ 项目升级到 Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当你首次打开在早期版本的 Visual Studio 中创建的 Visual C\+\+ 项目时，系统可能会提示你更新项目。 该消息会询问你是否想要升级到 Visual C\+\+ 编译器和库的最新版本。 升级的选项取决于用于创建该项目的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的版本。  
  
 你可以使用 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 打开、编辑和生成在 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 中创建的 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 项目，但要创建新的 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 项目，你必须使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]。 （若要创建 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 项目，必须使用 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]。）  
  
 若要创建 Windows 10 项目，必须使用 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)]。  
  
 如果没有提示你更新项目，则你可以不必执行任何操作来升级项目。 有关详细信息，请参阅 [移植、迁移和升级 Visual Studio 项目](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)。  
  
-   如果项目 \(.vcproj\) 是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之前的 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 版本中创建的，则你必须更新项目。  
  
-   如果项目 \(.vcxproj\) 是在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 或 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 中创建的，则你有两个选择：  
  
    -   你可以跳过更新。 如果 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 有权访问 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 或 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 中的 Visual C\+\+ 工具，则它将加载项目而不进行任何更改。 可以通过在具有 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 的同一台计算机上安装用于创建项目的 Visual Studio 版本，来提供此访问权限 。 有关详细信息，请参阅 [并行安装 Visual Studio 版本](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)。  
  
    -   你可以通过允许 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 进行本主题稍后所述的更改来更新项目。 如果你的解决方案中的 Visual C\+\+ 项目超过一个，则必须将它们全部更新。  
  
        > [!NOTE]
        >  如果你在系统首次提醒时拒绝更新，则可以稍后在“项目”菜单上选择“更新 VC\+\+ 项目”来更新项目。 如果此命令未出现，则不需要更新。  
  
## 升级 Visual C\+\+ 项目  
 如果你允许 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 自动更新项目，则要进行以下更改：  
  
-   更改项目以便它使用 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 编译器和库 \(PlatformToolset \= VisualStudio v140\)。  
  
-   对于 [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)] 项目，请将 TargetFrameworkVersion 更改为 .NET Framework 4.5.2。  
  
## 继续使用自定义 PlatformToolset  
 如果要继续在 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 中使用自定义的 PlatformToolset，则该工具集必须位于 x86 计算机的 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ 下，或位于 x64 计算机的 %ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ 下。 有关如何创建自定义 PlatformToolset 的信息，请参见 Visual C\+\+ 团队博客上的 [C\+\+ 本机多目标](http://go.microsoft.com/fwlink/?LinkId=248587)。  
  
## 请参阅  
 [移植、迁移和升级 Visual Studio 项目](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)