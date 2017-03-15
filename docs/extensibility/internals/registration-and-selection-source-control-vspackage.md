---
title: "注册和选择 (源控制 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 34
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 693955c38d4d53418a92357e54bfc7c2965bdc3e
ms.lasthandoff: 02/22/2017

---
# <a name="registration-and-selection-source-control-vspackage"></a>注册和选择 (源控制 VSPackage)
VSPackage 必须注册才能对其进行公开的源控件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如果注册多个源控件 VSPackage 时，用户可以选择在适当的时候加载的 VSPackage。 请参阅[Vspackage](../../extensibility/internals/vspackages.md)有关 VSPackages 迁移以及如何将它们注册的更多详细信息。  
  
## <a name="registering-a-source-control-package"></a>注册源代码管理包  
 源代码管理包注册，以便[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境可以找到它，并查询其支持的功能。 这一点符合仅在其功能或命令都是必需或显式请求时在其中创建包的实例的延迟加载方案。  
  
 Vspackage 将信息放在一个特定于版本的注册表项，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*，其中*X*是主版本号和*Y*是次版本号。 这种做法提供支持的多个版本的并行安装的能力[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用户界面 (UI) 以及源代码管理 Vspackage 支持从多个安装的源代码管理插件 （通过源代码管理适配器包） 中进行选择。 可以有只能有一个活动的源代码管理插件或 VSPackage 一次。 但是，如下所述，IDE 将允许的自动解决方案基于包交换机制通过源代码管理插件和 Vspackage 之间切换。 有一些部分 VSPackage 的源代码管理的要求，若要启用此选择机制。  
  
### <a name="registry-entries"></a>注册表项  
 源代码管理包需要三个私有 Guid:  
  
-   包 GUID︰ 这是包含源控件的实现 （在本部分中称为 ID_Package） 的包的主 GUID。  
  
-   源代码管理 GUID︰ 这是源代码管理用于向 Visual Studio 源控件存根 （stub） 注册的 VSPackage 的 GUID，也可以使用命令 UI 上下文 GUID。 源控件服务 GUID 注册受源代码管理 GUID。 在示例中，源代码管理 GUID 称为 ID_SccProvider。  
  
-   源控制服务的 GUID︰ 这是专用的服务 （在本部分中称为 SID_SccPkgService） 的 Visual Studio 使用的 GUID。 除此之外，源代码管理包需要定义其他 Guid 的 Vspackage，工具窗口，依次类推。  
  
 必须由源控件 VSPackage 进行以下注册表项︰  
  
|项名称|条目|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|（默认值） = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|（默认值） = rg_sz:\<包的友好名称&1;><br /><br /> 服务 = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|（默认值） = rg_sz: #\<本地化名称的资源 ID&1;><br /><br /> 包 = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (请注意，键名称， `SourceCodeControl`，已被使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]并不是可用的选择\<PackageName&1;>。)|（默认值） = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>选择源代码管理包  
 多个基于源控制插件 API 的插件和源代码的控制 Vspackage 可能同时进行注册。 选择源代码管理插件或 VSPackage 的过程都必须确保[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载插件或 VSPackage 在适当的时间，并可以推迟加载不必要的组件，直到它们是必需的。 此外，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必须从其他非活动状态的 Vspackage，包括菜单项、 对话框和工具栏，删除所有 UI 的情况并显示用户界面的活动的 VSPackage。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]执行以下操作之一时，将加载 VSPackage 的源控件︰  
  
-   （当该解决方案处于源代码管理之下），打开解决方案。  
  
     打开解决方案或项目受源代码管理时，IDE 会导致源代码管理已指定为该解决方案要加载的 VSPackage。  
  
-   执行任何源代码管理 VSPackage 的菜单命令。  
  
 使用了应该加载 VSPackage 仅时它们实际上将会出现所需的任何组件版本控制 （也称为延迟加载）。  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>自动解决方案基于 VSPackage 交换  
 您可以手动交换源代码管理 VSPackages 迁移通过[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**选项**对话框中的下**源代码管理**类别。 基于解决方案的包自动交换意味着打开该解决方案时，已指派给特定解决方案源代码管理包自动设置为活动状态。 每个源代码管理包应实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]处理两者之间进行切换源控制插件 （实现源控制插件 API） 和源代码控制 Vspackage。  
  
 源控件适配器包用于切换到任何基于源控制插件 API 的插件。 切换到中间的源控件适配器包并确定哪些源代码管理插件的过程必须设置为活动或非活动用户是透明的。 适配器包始终处于活动状态的任何源代码管理插件处于活动状态时。 切换到简单地加载和卸载插件 DLL 的两个源控制插件金额。 切换到源代码管理 VSPackage，但是，涉及与 IDE 以加载相应的 VSPackage 进行交互。  
  
 源代码管理打开任何解决方案并且为 VSPackage 的注册表项是在解决方案文件时，被调用 VSPackage。 打开解决方案时，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]查找注册表值并加载相应的源控件 VSPackage。 Vspackage 的所有源控件必须都具有上面所述的注册表项。 在源代码管理下的解决方案被标记为与特定的源代码管理 VSPackage 关联。 源的控件必须实现 Vspackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>为允许自动解决方案基于 VSPackage 换。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio 为包选择和切换用户界面  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供了源代码管理 VSPackage 的 UI 和插件中的选定内容**选项**对话框中的下**源代码管理**类别。 它允许用户选择的活动的源代码管理插件或 VSPackage。 下拉列表包括︰  
  
-   所有已安装的源代码管理包  
  
-   所有安装的源代码管理插件  
  
-   "None"选项，这将禁用源代码管理  
  
 仅用于该活动的源控件选择的用户界面是可见的。 VSPackage 所选内容的上一个 VSPackage 隐藏 UI，并显示新的 UI。 活动的 VSPackage 选择基于每个用户。 如果用户具有的多个副本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]同时打开，每个有可能使用不同的活动 VSPackage。 如果多个用户登录到同一台计算机，每个用户可以拥有的单独实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]打开，每个都有不同的活动 VSPackage。 当多个实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]由用户，源代码管理最后一个打开的解决方案将成为默认的源代码管理 VSPackage，若要设置活动在重新启动处于活动状态的 VSPackage 关闭。  
  
 与早期版本的不同[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，IDE 不再重新启动切换 Vspackage 的源代码管理的唯一方法。 VSPackage 所选内容是自动的。 切换包需要 Windows 用户权限 （不管理员或超级用户）。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [功能](../../extensibility/internals/source-control-vspackage-features.md)   
 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Vspackage](../../extensibility/internals/vspackages.md)
