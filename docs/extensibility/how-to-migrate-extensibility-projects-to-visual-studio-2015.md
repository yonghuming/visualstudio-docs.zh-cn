---
title: "如何︰ 将可扩展性项目迁移到 Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK，升级"
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何︰ 将可扩展性项目迁移到 Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下面介绍了如何升级您的扩展。  
  
> [!IMPORTANT]
>  如果您想要维护为早期版本的 Visual Studio 扩展解决方案的版本，请确保要在升级之前制作的副本。 它可能很难返回到其以前的状态的升级后的版本。  
  
#### 若要升级的可扩展性解决方案  
  
1.  你想要升级，请打开新的版本中使用的副本。 将会建议您升级是不可逆。  
  
2.  在升级完成后，更改到新版本的 devenv.exe 的外部程序的路径。 用鼠标右键单击中的项目节点 **解决方案资源管理器**, ，然后选择 **属性**。 在 **调试** 选项卡上，找到通过文本框中 **启动外部程序** 并将 devenv.exe 的路径更改为 Visual Studio 2015 路径，它应如下所示︰  
  
     **%ProgramFiles%\\Microsoft visual Studio 14.0\\Common7\\IDE\\devenv.exe**  
  
3.  添加对 Microsoft.VisualStudio.Shell.14.0.dll 的引用。 \(右键单击中的项目节点 **解决方案资源管理器** ，然后选择 **添加 \/ 引用**。 选择 **扩展** 选项卡上，然后检查 **Microsoft.VisualStudio.Shell.14.0**。\)  
  
4.  生成解决方案。 生成的文件部署到︰  
  
     **%LOCALAPPDATA%\\Microsoft\\VisualStudio.14.0Exp\\Extensions\\ \< 作者姓名 \> \\ \< 项目名称 \> \\ \< 项目版本 \> \\**。  
  
#### 若要向 NuGet VS SDK 引用程序集更新扩展性项目  
  
1.  确定你的项目需要的 VS SDK 引用程序集。  在 **解决方案资源管理器**, ，展开项目的 **引用** 节点并查看项目引用的列表。  VS SDK 引用程序集将具有前缀 **Microsoft.VisualStudio** 名称中 \(例如︰ Microsoft.VisualStudio.Shell.14.0\)。  
  
2.  VS SDK 引用程序集从项目中移除通过选择它们，然后右键单击和 **删除**。  
  
3.  添加 VS SDK 引用程序集的 NuGet 版本。  在仍处于 **解决方案资源管理器中引用** 节点，打开 **管理 NuGet 包...** 对话框。  如果你想要了解有关此对话框的详细信息，请参阅 [使用对话框管理 NuGet 包](http://docs.nuget.org/Consume/Package-Manager-Dialog)。 VS SDK 引用程序集在上发布 [nuget.org](http://www.nuget.org) 通过 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)。  
  
4.  使用 **nuget.org** 作为您 **包源**, ，搜索匹配所需的引用程序集的 NuGet 包名称 \(例如︰ Microsoft.VisualStudio.Shell.14.0\) 并将其安装在您的项目。  NuGet 可以添加多个引用程序集以满足初始程序集的依赖关系。  
  
     如果您愿意，您可以通过安装 VS SDK 一次性添加所有 VS SDK 引用程序集 [元程序包](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。  
  
5.  此外可以切换到使用 VS SDK 生成工具的 NuGet 版本。 此 NuGet 程序包是 [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) 并一次添加到您的项目将包含所需的工具和目标文件，以使您的计算机上建立扩展性项目，而无需安装了 VS SDK。  
  
> [!NOTE]
>  它不需要更新您现有的可扩展性项目，以便使用 NuGet 引用程序集和工具。  它们可以继续使用引用程序集和与 VS SDK 一起安装的工具进行构建。