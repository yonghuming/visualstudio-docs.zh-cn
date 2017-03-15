---
title: "扩展分析器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage, 加载失败分析器"
ms.assetid: 8d2bcc4e-9feb-45a5-8d8e-470346f0d39e
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# 扩展分析器
“扩展分析器”捕获和记录最常见的扩展加载失败。 “扩展分析器”在其自己的工具窗口中运行。 分析器报告失败原因，并提出有关如何修复的建议。  
  
 可以从 Visual Studio 库中下载[扩展分析器](http://go.microsoft.com/fwlink/?LinkId=205840)。 “扩展分析器”程序集安装在 \<*Visual Studio 安装路径*\>\\Common7\\IDE\\PrivateAssemblies\\ 下。  
  
## 浏览者  
 安装“扩展分析器”后，请在“工具”菜单上单击“扩展分析器”，再单击“浏览器”。 将显示一个窗口，窗口列出了在计算机上注册的所有扩展。 针对 VSIX 文件、VSPackage、PkgDef 文件和 MEF 组件有不同的选项卡。 可以按任何列名称对列表排序。  
  
1.  VSIX 选项卡显示有关已安装的 VSIX 扩展的信息。 可以通过选中“显示系统组件”复选框来包含系统组件。 在此选项卡上，可以导航到 VSIX 日志条目，在 Visual Studio XML 编辑器中打开 VSIX 清单，并打开安装 VSIX 扩展的文件夹。  
  
2.  VS 包选项卡显示 Visual Studio 当前已知的有关 VSPackage 的信息，无论它们是否已加载。 此信息包括 VSIX 标识符、.pkgdef 文件和 VSPackage 的 GUID。 可以通过选中“显示系统包”复选框来包含系统 VSPackage。 在此选项卡上，可以导航到日志条目，查看 VSIX 选项卡上列出的 VSIX，查看 PkgDef 文件选项卡上的.pkgdef 文件并分析 VSPackage。 分析结果显示在“输出”窗格中。  
  
3.  PkgDef 文件选项卡显示 Visual Studio 已知的有关.pkgdef 扩展文件的信息。 此信息包括 VSIX 标识符和扩展路径。 可以导航到日志或 VSIX 选项卡上，并且可以在编辑器中查看.pkgdef 文件。  
  
4.  MEF 组件选项卡显示 Visual Studio 已知的有关 MEF 组件的信息。 此信息包括 VSIX 标识符和扩展的安装路径。 可以通过选中“显示系统组件”复选框来包含系统组件。 此外，还可以导航到相应的 VSIX 条目、.pkgdef 文件和扩展的安装位置。  
  
> [!WARNING]
>  可能会收到一条请求你打开合成日志记录的消息。 若要这样做，请选择日志文件的位置。 可能需要在继续操作之前重新启动 Visual Studio 的所有实例。  
  
## 日志查看器  
 如果正在运行已打开日志记录的项目（通过将日志添加到项目的命令行参数），则可以通过“扩展日志查看器”查看日志记录消息。 有关详细信息，请参阅[\/Log](../ide/reference/log-devenv-exe.md)。 “扩展日志查看器”窗口将显示日期、侦听器、条目类型（消息类型）、错误类型、类\/接口信息和日志消息。 可以对信息进行排序和筛选。  
  
## 常见的扩展加载问题  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中加载扩展失败的一些典型原因是：  
  
-   依赖项问题。 扩展可能已经以无法找到依赖程序集的方式部署。  
  
-   异常。 加载 VSPackage 时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调用其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 方法。 如果此方法引发异常，则 VSPackage 加载失败。 隔离此问题的最佳方法是单步执行 SetSite 代码。  
  
-   不正确的注册。 请验证是否对扩展正确地签名以及是否使用正确的公钥注册 VSPackage。  
  
## 请参阅  
 [管理 Vspackage](../extensibility/managing-vspackages.md)