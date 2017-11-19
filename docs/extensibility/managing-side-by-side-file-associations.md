---
title: "管理并排显示文件关联 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dfb3bcca8c56ebefa665e44384df0751e71f6591
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managing-side-by-side-file-associations"></a>管理并排显示文件关联
如果你的 VSPackage 提供的文件关联，你必须决定如何处理在其中通过并行安装的特定版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]应被调用来打开文件。 文件格式不兼容复合问题。  
  
 用户期望的产品是与早期版本中，兼容的以便可以在新版本中而不会丢失数据加载现有文件的新版本。 理想情况下，你的 VSPackage 可以同时加载和保存早期版本的文件格式。 如果不是这样，你应提供的用于升级到你的 VSPackage 的最新版本的文件格式。 此方法的缺点是，无法在早期版本中打开升级的文件。  
  
 若要避免此问题，可以更改扩展时的文件格式变得不兼容。 例如，版本 1 的你的 VSPackage 可以使用扩展、.mypkg10 和 2 无法使用扩展，版本.mypkg20。 这种差异标识打开特定文件的 VSPackage。 如果你将较新的 Vspackage 添加到与旧扩展名相关联的程序列表中，用户可以右键单击该文件，并选择在较新的 VSPackage 中打开它。 此时，你的 VSPackage 可提供的用于升级到新格式的文件或打开文件并保持与早期版本的 VSPackage 兼容性。  
  
> [!NOTE]
>  你可以结合使用这些方法。 例如，你可以通过将较旧文件加载提供向后兼容性，并为提供时用户将其保存升级的文件格式。  
  
## <a name="facing-the-problem"></a>面向问题  
 如果你想要使用相同的扩展的多个并排显示 Vspackage，你必须选择的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]扩展与该键相关联。 以下是两种替代方法：  
  
-   打开中的最新版本的文件[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用户的计算机上安装。  
  
     在此方法时，安装程序，负责确定的最新版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和包括所写入的文件关联的注册表项中。 在 Windows Installer 包中，你可以包括自定义操作以便设置一个属性，指示的最新版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
    > [!NOTE]
    >  在此上下文中，"最新"意味着"最新支持的版本"。 这些安装程序项将不会自动检测的后续版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 中的条目[检测系统要求](../extensibility/internals/detecting-system-requirements.md)并在[命令，必须将运行之后安装](../extensibility/internals/commands-that-must-be-run-after-installation.md)是类似于此处所述，支持的其他版本所需[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     CustomAction 表中的以下行设置 DEVENV_EXE_LATEST 属性可由 AppSearch 设置的属性和 RegLocator 表中所述[命令，必须将运行之后安装](../extensibility/internals/commands-that-must-be-run-after-installation.md)。 InstallExecuteSequence 表中的行计划尽早执行序列中的自定义操作。 条件列进行的逻辑工作中的值：  
  
    -   如果它是仅存在版本，visual Studio.NET 2002年将是最新版本。  
  
    -   Visual Studio.NET 2003年是最新版本，仅当存在和[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]不存在。  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]如果它是仅存在版本，是最新版本。  
  
     最终结果是 DEVENV_EXE_LATEST 包含 devenv.exe 的最新版本的路径。  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>确定最新版本的 Visual Studio 的 CustomAction 表行  
  
    |操作|类型|源|目标|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>确定最新版本的 Visual Studio 的 InstallExecuteSequence 表行  
  
    |操作|条件|序列|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 和 NOT （DEVENV_EXE_2003 或 DEVENV_EXE_2005）|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 和不 DEVENV_EXE_2005|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     可以使用 Windows Installer 包的注册表表中的 DEVENV_EXE_LATEST 属性编写 HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand 密钥的默认值，[DEVENV_EXE_LATEST]"%1"  
  
-   运行可以做出最佳选择从可用 VSPackage 版本共享的启动器程序。  
  
     开发人员确定的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]选择这种方法来处理复杂的需求的解决方案和项目所产生的多个版本的多个格式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在此方法中，你将启动器程序注册为扩展处理程序。 启动器检查该文件，并决定哪个版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]并且你的 VSPackage 可以处理该特定的文件。 例如，如果用户打开自上次保存你的 VSPackage 的特定版本的文件，启动器可以启动该 VSPackage 中匹配的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 此外，用户无法配置启动器始终启动最新版本。 启动程序还可能提示用户升级文件的格式。 如果文件的格式包括版本号，启动器无法从版本晚于一个或多个已安装的 Vspackage 的文件格式是否通知用户。  
  
     启动程序应为与你的 VSPackage 的所有版本共享的 Windows Installer 组件。 此过程可确保最新版本始终安装，并且不会删除它，直到卸载你的 VSPackage 的所有版本。 这种方式，文件关联和启动程序组件的其他注册表项会保留即使卸载的 VSPackage 的一个版本。  
  
## <a name="uninstall-and-file-associations"></a>卸载和文件关联  
 卸载写入文件关联的注册表项的 VSPackage 中删除的文件关联。 因此，扩展插件没有任何关联的节目。 Windows Installer 未"恢复"安装 VSPackage 时已添加的注册表项。 以下是解决用户的文件关联的一些方法：  
  
-   使用共享的启动器组件，如上文所述。  
  
-   指示用户运行版本的用户想要拥有文件关联的 VSPackage 的修复。  
  
-   提供一个单独的可执行程序，用于重写相应的注册表项。  
  
-   提供配置选项的页面或对话框框中，从而让用户选择文件关联，并回收丢失的关联。 指示用户卸载后运行它。  
  
## <a name="see-also"></a>另请参阅  
 [注册-并排部署的文件扩展名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [注册文件扩展名的谓词](../extensibility/registering-verbs-for-file-name-extensions.md)