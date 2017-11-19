---
title: "注册和选择 (源控件 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 118f715e71f610d4e9dc2589767f6fb54ab4e814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="registration-and-selection-source-control-vspackage"></a>注册和选择 (源控件 VSPackage)
必须注册 VSPackage 来公开到源代码管理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如果注册多个源控件 VSPackage 时，用户可以选择哪些 VSPackage 加载在适当的时间。 请参阅[Vspackage](../../extensibility/internals/vspackages.md)有关 Vspackage 以及如何对它们进行注册的更多详细信息。  
  
## <a name="registering-a-source-control-package"></a>注册源代码管理包  
 注册源代码管理包，以便[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境可以查找它，并查询其支持的功能。 这是根据其功能或命令需要或明确地提出请求时，仅在其中创建包的实例的延迟加载方案。  
  
 Vspackage 将信息放在一个特定于版本的注册表项，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*，其中*X*是的主版本号和*Y*是次要版本号。 这种做法使能够支持通过并行安装多个版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用户界面 (UI) 以及源代码管理 Vspackage 支持从多个已安装的源控件插件 （通过源代码管理适配器包） 的选择。 可以有一个活动的源代码管理插件或 VSPackage 一次。 但是，如下所述，IDE 会允许通过自动基于解决方案包交换机制的源控件插件和 Vspackage 之间切换。 有一些部分的源控件 VSPackage 的要求，若要启用此选择机制。  
  
### <a name="registry-entries"></a>注册表项  
 源代码管理包需要三个私有 Guid:  
  
-   包 GUID： 这是包含 （在本部分中称为 ID_Package） 的源控件实现的包的主要 GUID。  
  
-   源代码管理 GUID： 这是用于向 Visual Studio 源控件存根注册 VSPackage 的源控件的 GUID，也用作命令 UI 上下文 GUID。 在源代码管理 GUID 下注册源控件服务 GUID。 在示例中，源控件 GUID 称为 ID_SccProvider。  
  
-   源控件服务 GUID： 这是专用的服务 （在本部分中称为 SID_SccPkgService） 的 Visual Studio 使用的 GUID。 除此之外，源代码管理包需要定义其他 Guid 的 Vspackage，工具窗口，依次类推。  
  
 通过源代码管理 VSPackage 必须将下列注册表项：  
  
|项名称|条目|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|（默认值） = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|（默认值） = rg_sz:\<包的友好名称 ><br /><br /> 服务 = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|（默认值） = rg_sz: #\<本地化名称的资源 ID ><br /><br /> 包 = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (请注意，键名称， `SourceCodeControl`，已被使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，不能作为选择\<PackageName >。)|（默认值） = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>选择源代码管理包  
 多个基于源控制插件 API 的插件和源代码的管理可能同时注册 Vspackage。 选择源代码管理插件或 VSPackage 的过程必须确保[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载插件或 VSPackage 在适当的时间，并可以推迟加载不必要的组件，直到它们是必需的。 此外，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必须从其他非活动状态的 Vspackage，包括菜单项、 对话框和工具栏，删除所有的 UI，并显示为活动的 VSPackage 的 UI。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载源代码管理 VSPackage 时执行以下操作之一：  
  
-   （当解决方案时在源代码管理下），打开解决方案。  
  
     当打开解决方案或项目受源代码管理时，IDE 将导致源代码管理已指定为要加载该解决方案的 VSPackage。  
  
-   执行的任何源控件 VSPackage 的菜单命令。  
  
 VSPackage 应加载仅时它们实际上会成为所需的任何组件的源控件使用 （也称为延迟加载）。  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>自动基于解决方案的 VSPackage 交换  
 你可以手动交换源代码管理 Vspackage 通过[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**选项**对话框中的下**源代码管理**类别。 基于解决方案包自动交换意味着打开该解决方案时，已指派给特定解决方案源代码管理包自动设置为活动。 每个源代码管理包应实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]处理这两个之间交换机源控件的插件 （实现源控件插件 API） 和源控件，Vspackage。  
  
 源代码管理适配器包用于切换到任何基于源控制插件 API 的插件。 切换到中间的源控件适配器包并确定哪些源代码管理插件的过程必须设置为活动或非活动用户是透明的。 适配器包始终处于活动状态的任何源代码管理插件处于活动状态时。 只需加载和卸载插件 DLL 的两个源控制插件金额之间切换。 切换到源控件 VSPackage，但是，涉及 IDE 加载相应的 VSPackage，与之进行交互。  
  
 源代码管理打开的任何解决方案和 VSPackage 的注册表项是在解决方案文件时调用 VSPackage。 当打开解决方案时，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]查找注册表值并加载相应的源控件 VSPackage。 所有源控件 Vspackage 必须都具有上面所述的注册表项。 在源代码管理下的解决方案被标记为正在与特定的源代码管理 VSPackage 关联。 源的控件，Vspackage 必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>若要启用自动基于解决方案的 VSPackage 交换。  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio 为包选择和切换用户界面  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供用于源代码管理 VSPackage 的 UI 和中的插件选定内容**选项**对话框中的下**源代码管理**类别。 它允许用户选择活动的源代码管理插件或 VSPackage。 下拉列表包括：  
  
-   所有已安装的源代码管理包  
  
-   所有安装的源代码管理插件  
  
-   "无"选项，这将禁用源代码管理  
  
 仅选择此活动的源控件 UI 是可见的。 VSPackage 选择为以前的 VSPackage 中隐藏用户界面，并显示新的 UI。 活动的 VSPackage 选择基于每个用户。 如果用户具有的多个副本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]同时打开，每个可能可以使用不同的活动 VSPackage。 如果多个用户登录到同一台计算机，每个用户可以拥有的单独实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]打开，每个都有不同的活动 VSPackage。 时的多个实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]关闭的用户，最后一个打开的解决方案成为默认的源代码管理 VSPackage，若要设置活动在重新启动处于活动状态的 VSPackage 的源控件。  
  
 与以前版本的不同[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，IDE 不再重新启动切换 Vspackage 的源代码管理的唯一方法。 VSPackage 选择是自动的。 切换包需要 Windows 用户特权 （不管理员或超级用户）。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [功能](../../extensibility/internals/source-control-vspackage-features.md)   
 [创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackage](../../extensibility/internals/vspackages.md)