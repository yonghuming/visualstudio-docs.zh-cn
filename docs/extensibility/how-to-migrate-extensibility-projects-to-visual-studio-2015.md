---
title: "如何： 将扩展性项目迁移到 Visual Studio 2015 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 016e609acb7ad837580b4cabb6055169ac7357c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>如何： 将扩展性项目迁移到 Visual Studio 2015
下面介绍了如何升级你的扩展。  
  
> [!IMPORTANT]
>  如果你想要维护的扩展解决方案中为 Visual Studio 的早期版本的版本，请务必在升级之前，请创建一个副本。 它可能很难返回到其以前状态的升级的版本。  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>若要升级的扩展性解决方案  
  
1.  你想要升级，请打开新的版本中使用的副本。 你将建议升级是不可逆。  
  
2.  在升级完成后，将该外部程序的路径更改 devenv.exe 的新版本。 右键单击中的项目节点**解决方案资源管理器**，然后选择**属性**。 在**调试**选项卡上，找到通过文本框中**启动外部程序**并将 devenv.exe 的路径更改为 Visual Studio 2015 路径，这应如下所示：  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  添加对 Microsoft.VisualStudio.Shell.14.0.dll 的引用。 (右键单击中的项目节点**解决方案资源管理器**，然后选择**添加 / 参考**。 选择**扩展**选项卡上，然后检查**microsoft.visualstudio.shell.14.0 的引用**。)  
  
4.  生成解决方案。 将生成的文件被部署到:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 创作名称\>\\< 项目名称\>\\< 项目版本\>\\** .  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>若要更新扩展性项目以 NuGet VS SDK 引用程序集  
  
1.  确定你的项目需要的 VS SDK 引用程序集。  在**解决方案资源管理器**，展开项目的**引用**节点并查看项目引用的列表。  VS SDK 引用程序集将具有前缀**Microsoft.VisualStudio**名称中 (例如： microsoft.visualstudio.shell.14.0 的引用)。  
  
2.  从项目中删除 VS SDK 引用程序集，通过选择它们，右键单击和**删除**。  
  
3.  添加 VS SDK 引用程序集的 NuGet 版本。  仍中时，在**解决方案资源管理器引用**节点，打开**管理 NuGet 包...**对话框。  如果你想要了解有关此对话框的详细信息，请参阅[包管理器 UI](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI)。 VS SDK 引用程序集在上发布[nuget.org](http://www.nuget.org)通过[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)。  
  
4.  使用**nuget.org**作为你**包源**，搜索匹配的所需的引用程序集的 NuGet 包名称 (例如： microsoft.visualstudio.shell.14.0 的引用) 并安装在你项目。  NuGet 可以添加多个引用程序集，以满足初始程序集的依赖关系。  
  
     如果你愿意，你可以通过安装 VS SDK 一次性添加所有 VS SDK 引用程序集[元包](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。  
  
5.  此外可以切换到使用 VS SDK 生成工具的 NuGet 版本。 此 NuGet 程序包是[Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools)并一次添加到你的项目将包含所需的工具和目标文件，以便你可以在计算机上生成扩展性项目，而无需安装的 VS SDK。  
  
> [!NOTE]
>  它不是所需更新现有扩展性项目以使用 NuGet 引用程序集和工具。  它们可以继续使用引用程序集和与 VS SDK 一起安装的工具进行生成。