---
title: "故障排除 Vspackage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>VSPackages 迁移故障排除
以下是常见的问题，可能有你的 VSPackage，并解决问题的提示。  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>若要解决可防止 Visual Studio 启动的 VSPackage  
  
-   启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式下。  
  
     若要启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式下，在命令提示符处，键入**devenv.exe /safemode**。  
  
     在此过程中没有 Vspackage 加载除附带 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>若要解决不会加载 VSPackage  
  
1.  请确保您正在使用注册 VSPackage 若要运行，通常的实验性的注册表根目录的注册表根目录。  
  
     有关详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
2.  如果 VSPackage 针对在实验性的注册表根目录中运行，请确保您正在运行的实验版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     若要运行的实验版本，请在命令窗口中键入以下︰ **devenv /rootsuffix exp**。  
  
3.  请检查 VSPackage 的注册表条目。  
  
     有关详细信息，请参阅[注册 VSPackages 迁移](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)和[管理 VSPackages 迁移](../extensibility/managing-vspackages.md)。  
  
4.  打开**输出**窗口的实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]未能加载 VSPackage。 有关为什么 VSPackage 无法加载的信息可能显示在该窗口中。  
  
    > [!NOTE]
    >  如果您启动的实验版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]从[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)，检查**输出**窗口中的两个版本。  
  
5.  检查活动日志。  
  
     有关详细信息，请参阅[如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
6.  有关由 IDE 引发的异常详细信息，请单击**异常**上**调试**菜单启用例外。 在**异常**对话框中选择要了解详细信息的异常的类型。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>若要解决不会注册的 VSPackage  
  
1.  请确保 VSPackage 程序集位于受信任的位置。 RegPkg 无法在受信任的或部分受信任的位置，例如默认的.net 安全配置中的网络共享中注册程序集。 每当用户在不受信任位置中创建一个项目时，会出现一个警告，尽管"不再显示此消息"复选框可防止再次出现此警告。  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>若要解决不可见或，将生成错误，当您单击的命令的命令  
  
1.  通过键入以下内容合并新的或更改菜单命令和那些已在 IDE 中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示符︰ **devenv /rootsuffix Exp /setup**。  
  
2.  请确保[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]UI.dll 查找你的 VSPackage。  
  
    1.  在注册表的程序包部分中找到的 VSPackage 的 CLSID:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<版本&1;>*\Packages  
  
    2.  验证给定由 SatelliteDll 子项的路径正确。  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>若要解决意外的行为的 VSPackage  
  
1.  在代码中设置断点。  
  
     好的调试起点是构造函数，并初始化方法。 此外可以用来计算，如菜单命令的区域中设置断点。 若要启用断点，必须在调试器下运行。  
  
    1.  在**项目**菜单上，单击**属性**。  
  
    2.  在**属性页**对话框中，选择**调试**选项卡。  
  
    3.  在**命令行参数**框中，键入在开发环境的根后缀的 VSPackage 目标。 例如，若要选择的实验性生成，请键入︰ **RootSuffix Exp**。  
  
    4.  在**调试**菜单上，单击**开始调试**或按 F5。  
  
        > [!NOTE]
        >  如果正在调试一个项目，创建或现在加载你的项目的现有实例。  
  
2.  使用活动日志。  
  
     通过将信息写入活动日志，以在关键点跟踪 VSPackage 行为。 零售环境中运行 VSPackage 时，此技术是特别有用。 有关详细信息，请参阅[如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
3.  使用公共符号。  
  
     若要在调试时提高可读性，可以附加到调试器符号。  
  
    1.  从**工具/选项**菜单上，导航到**调试/符号**对话框。  
  
    2.  添加此**符号文件 (.pdb) 位置**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  为了提高性能，请指定符号缓存文件夹，例如︰  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>缺少 VSPackage 或其依赖项之一进行故障排除  
  
1.  对于托管代码中，请确保引用路径正确。  
  
    1.  在**项目**菜单上，单击**属性**。  
  
    2.  选择**引用**选项卡中**属性页**对话框，并确保所有路径都是否正确。 或者，可以使用**对象浏览器**浏览引用的对象。  
  
         对于托管代码中，您可以使用[Fuslogvw.exe （程序集绑定日志查看器）](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296)显示失败的程序集加载的详细信息。  
  
2.  对于非托管代码中，找到的 VSPackage 中 CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID 注册表节点︰  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<版本&1;>*\CLSID  
  
 请确保 InprocServer32 条目具有 VSPackage dll 的正确路径。  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage](../extensibility/internals/vspackages.md)
