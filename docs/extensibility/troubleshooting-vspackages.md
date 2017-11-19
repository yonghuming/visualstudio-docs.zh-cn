---
title: "关于 Vspackage 的疑难解答 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e409d31b4f1e16f735b9b4ef22d42dedccf55a9d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-vspackages"></a>故障排除的 Vspackage
以下是常见的问题，你可能必须与你的 VSPackage 并解决问题的提示。  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>若要解决 VSPackage 并使 Visual Studio 保持启动  
  
-   启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式下。  
  
     若要启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式下，在命令提示符处，键入**devenv.exe /safemode**。  
  
     在此过程中没有 Vspackage 加载除外附带 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>若要解决不会加载 VSPackage  
  
1.  请确保你正在使用在其中注册 VSPackage 来运行，通常的实验性注册表根注册表根目录。  
  
     有关详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
2.  如果 VSPackage 的目标是在实验注册表根目录中运行，请确保您正在运行的实验版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     若要运行的实验版本，可在命令窗口中键入以下： **devenv /rootsuffix exp**。  
  
3.  请检查 VSPackage 的注册表条目。  
  
     有关详细信息，请参阅[注册 Vspackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)和[管理 Vspackage](../extensibility/managing-vspackages.md)。  
  
4.  打开**输出**的实例的窗口[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]未能加载 VSPackage。 有关失败 VSPackage 加载的原因的信息可能显示在该窗口中。  
  
    > [!NOTE]
    >  如果你刚刚启动的实验版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]从[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 中，检查**输出**的这两个版本的窗口。  
  
5.  检查活动日志。  
  
     有关详细信息，请参阅[如何： 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
6.  有关由 IDE 引发的异常的详细信息，请单击**异常**上**调试**菜单启用例外。 在**异常**对话框中选择的要了解详细信息的异常的类型。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>若要解决未注册 VSPackage  
  
1.  请确保 VSPackage 程序集位于受信任的位置。 RegPkg 无法在受信任的或部分受信任的位置，例如在默认.net 安全配置的网络共享中注册程序集。 尽管只要用户在不受信任的位置创建一个项目，会出现一个警告，"不再显示此消息"复选框可以避免发生此警告。  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>若要解决的命令不可见，或当你单击的命令，用来生成错误  
  
1.  通过键入以下内容合并新的或更改菜单命令和已在 IDE 中的那些[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示符： **devenv /rootsuffix Exp /setup**。  
  
2.  请确保[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]UI.dll 查找你的 VSPackage。  
  
    1.  在注册表的包部分中找到的 VSPackage 的 CLSID:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<版本 >*\Packages  
  
    2.  验证给定 SatelliteDll 子项的路径正确。  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>若要解决出现异常行为的 VSPackage  
  
1.  在代码中设置断点。  
  
     用于调试的良好起点是构造函数和初始化方法。 你还可以在你想要评估，如菜单命令的区域设置断点。 若要启用断点，必须在调试器下运行。  
  
    1.  在“项目”菜单上，单击“属性”。  
  
    2.  上**属性页**对话框中，选择**调试**选项卡。  
  
    3.  在**命令行自变量**框中，键入开发环境的根后缀，VSPackage 目标。 例如，若要选择的实验性生成，请键入： **RootSuffix Exp**。  
  
    4.  上**调试**菜单上，单击**启动调试**或按 F5。  
  
        > [!NOTE]
        >  如果你正在调试的项目，创建或现在加载你的项目的现有实例。  
  
2.  使用活动日志。  
  
     通过将信息写入到在关键点的活动日志跟踪 VSPackage 行为。 在零售环境中运行 VSPackage 时，此方法十分特别有用。 有关详细信息，请参阅[如何： 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
3.  使用公共符号。  
  
     若要在调试时提高可读性，你可以附加到调试器的符号。  
  
    1.  从**工具/选项**菜单上，导航到**调试/符号**对话框。  
  
    2.  添加此**符号文件 (.pdb) 位置**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  若要提高性能，请指定一个符号缓存文件夹中，例如：  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>缺少 VSPackage 或其依赖项之一进行故障排除  
  
1.  对于托管代码中，请确保引用路径正确。  
  
    1.  在“项目”菜单上，单击“属性”。  
  
    2.  选择**引用**选项卡中**属性页**对话框，并确保所有路径都是否正确。 或者，可以使用**对象浏览器**浏览引用的对象。  
  
         对于托管代码中，你可以使用[Fuslogvw.exe （程序集绑定日志查看器）](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer)显示失败的程序集加载的详细信息。  
  
2.  对于非托管代码，查找在 VSPackage 的 CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID 注册表节点：  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<版本 >*\CLSID  
  
 请确保该 InprocServer32 项具有的 VSPackage dll 的正确路径。  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../extensibility/internals/vspackages.md)