---
title: "并行安装 Visual Studio 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "并行安装 [Visual Studio]"
  - "帮助 [Visual Studio], 安装"
  - "速成版 [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 并行安装 Visual Studio 版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在已安装早期版本的计算机上安装此版本的 Visual Studio。 如果遇到安装故障，则可以使用[日志收集工具](http://go.microsoft.com/fwlink/?LinkId=262077)收集有关故障的信息，以便可以自行调试问题。  
  
> [!NOTE]
>  建议您按照发布顺序来安装不同版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 例如，在安装 Visual Studio 2015 之前安装 Visual Studio 2013。  
  
 在并行安装各版本之前，您应该了解以下情况：  
  
-   如果使用 Visual Studio 2015 打开在 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 中创建的解决方案，则稍后可以在旧版本中再次打开和修改该解决方案，前提是你没有执行任何 Visual Studio 2015 特有的功能。  
  
-   如果你尝试使用 Visual Studio 2015 打开在 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 或更早的版本中创建的解决方案，则可能需要修改你的项目和文件才能与 Visual Studio 2015 兼容。 有关详细信息，请参阅 [移植、迁移和升级 Visual Studio 项目](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)。  
  
-   如果在已安装多个版本的计算机上卸载 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的一个版本，则将为所有版本移除 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的文件关联。 通过使用**“选项”**对话框的**“常规”**页上的**“环境”**中的[“还原文件关联”](../ide/reference/general-environment-options-dialog-box.md)按钮，可以重新映射这些文件关联。  
  
-   因为并非所有扩展都兼容，所以 Visual Studio 不会自动升级扩展。 必须从 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkId=178891) 或软件发行者处重新安装扩展。  
  
## .NET Framework 版本和并行安装  
  
-   Visual Basic、Visual C\# 和 Visual F\# 项目使用**“项目设计器”**中的**“目标框架”**选项来指定项目使用的 .NET Framework 版本。 对于 C\+\+ 项目，您可以通过修改 .vcxproj 文件手动更改目标框架。 有关详细信息，请参阅 [版本兼容性](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)。  
  
     创建项目时，可以在**“新建项目”**对话框中的**“.NET Framework”**列表中指定项目针对的 .NET Framework 版本。  
  
     有关语言特定的信息，请参见下表中的相应主题。  
  
    |语言|主题|  
    |--------|--------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[“项目设计器”, “应用程序”页 \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[“项目设计器”\-\>“应用程序”页 \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[配置项目](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[如何：修改目标框架和平台工具集](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../extensibility/debugger/includes/jsprjscript_md.md)]|[在公共语言运行时的上一版本上运行 JScript 应用程序](http://msdn.microsoft.com/zh-cn/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## 请参阅  
 [安装 Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [移植、迁移和升级 Visual Studio 项目](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [版本兼容性](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [安装 Visual Studio 的多个语言版本](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [生成 C\/C\+\+ 独立应用程序和并行程序集](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)