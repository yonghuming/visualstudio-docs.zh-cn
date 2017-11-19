---
title: "VSPackage 安装方案 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2128d4c2659d7e6e389384c4bf7e133a4fb32e47
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 安装方案
请务必设计灵活性到 VSPackage 安装程序。 例如，你可能需要时常释放安全修补程序在将来，或可能更改要求彻底的并行版本控制支持业务策略。  
  
 在[支持多个 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)，你可以阅读的优点和支持的通过并行安装的问题[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]与你的 VSPackage 的共享或通过并行安装。 简单地说，通过并行 Vspackage 提供最大的灵活性以支持新功能的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 本主题中讨论的方案不是唯一的选择，但它们显示为建议的最佳做法。  
  
## <a name="components-privacy-and-sharing"></a>组件、 隐私和共享  
  
##### <a name="make-your-components-independent"></a>使你的组件独立  
 一旦确定，并填充一个组件，将分配`GUID`，并将组件部署，则无法更改其构成。 如果您更改组件的组合，生成的组件必须具有一个新的新组件`GUID`。 提供这些事实，通过使每个组件独立的以及独自单元能够提供最大的版本控制灵活性。 有关适用于组件的规则的详细信息，请参阅[更改组件代码](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx)和[后会发生什么组件规则被破坏？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)。  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>不混用组件中的共享和私有资源  
 在组件级别上发生的引用计数。 因此，混合使用一个组件中的共享和私有资源使得无法更新专用资源，如可执行文件，而不会还覆盖共享的资源。 这种情况下创建向后兼容性问题，并将限制你创建的并行功能。  
  
 例如，使用注册表值来注册你的 VSPackage 与[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]应保留在组件中独立于用来注册你的 VSPackage 与[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 共享的文件或注册表值进入另一个组件。  
  
## <a name="scenario-1-shared-vspackage"></a>方案 1： 共享的 VSPackage  
 在此方案中，共享 VSPackage (支持的多个版本的单个二进制文件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) 在 Windows Installer 包中提供。 注册的每个版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]受用户可选择的功能。 它还意味着，当分配给单独的功能，每个组件可以选择单独的安装或卸载，使用户具有控制将 VSPackage 集成到不同版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 (请参阅[Windows 安装程序功能](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx)有关使用 Windows Installer 程序包中的功能的详细信息。)  
  
 ![VS 共享 vs 包图](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")  
共享的 VSPackage 安装程序  
  
 图中所示，共享的组件进行 Feat_Common 功能，始终安装的一部分。 通过使 Feat_VS2002 和 Feat_VS2003 功能可见，用户可以选择在安装时到哪些版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]他们想 VSPackage 可以集成。 用户还可以使用 Windows Installer 维护模式来添加或删除功能，在这种情况下添加或从的不同版本中移除的 VSPackage 注册信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
> [!NOTE]
>  将一项功能的显示列设置为 0 将隐藏它。 低级别的列的值，如 1，可确保将始终安装它。 有关详细信息，请参阅[INSTALLLEVEL 属性](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx)和[功能表](http://msdn.microsoft.com/library/aa368585.aspx)。  
  
## <a name="scenario-2-shared-vspackage-update"></a>方案 2： 共享的 VSPackage 更新  
 在此方案中，发运 VSPackage 安装在方案 1 的更新的版本。 方便讨论，更新添加了对支持[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，但它也可能是更简单的安全修补程序或 bug 修复服务包。 安装较新的组件的 Windows Installer 规则要求已在系统上的不变的组件不会再次复制。 在这种情况下，用于版本 1.0 已存在的系统将覆盖更新的组件 Comp_MyVSPackage.dll 并使用户可以选择添加新功能 Feat_VS2005 与 Comp_VS2005_Reg 其组件。  
  
> [!CAUTION]
>  每当在多个版本间共享 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，这至关重要的 VSPackage 的后续版本，保持与以前版本的向后兼容[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 不能保持向后兼容，你必须使用并排显示、 专用的 Vspackage。 有关详细信息，请参阅[支持多个 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
 ![VS 共享 VS 包更新图像](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")  
共享 VSPackage 更新安装程序  
  
 此方案提供了一个新的 VSPackage 安装程序，利用小规模的升级的 Windows 安装程序的支持。 用户只需安装 1.1 版和 1.0 版，它将升级。 但是，不需要具有在系统上的版本 1.0。 相同的安装程序将没有 1.0 版的系统上安装版本 1.1。 若要提供这种方式的次要升级的优点是不需要经历的开发的升级的安装程序和完整产品安装程序的工作。 一个安装程序执行两个作业。 安全修补程序或服务包可能会改为利用 Windows Installer 修补程序。 有关详细信息，请参阅[修补和升级](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)。  
  
## <a name="scenario-3-side-by-side-vspackage"></a>方案 3： 通过并行 VSPackage  
 此方案提供了两个 VSPackage 安装程序-一个用于每个版本的 Visual Studio.NET 2003年和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 每个安装程序安装的并行安装或专用，VSPackage (一个专门生成和为特定版本的安装[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)])。 每个 VSPackage 是其自己的组件中。 因此，每个可以单独服务的修补程序或具有维护释放。 由于 VSPackage DLL 现在是特定于版本的可安全地与 DLL 相同的组件中包括其注册信息。  
  
 ![VS 端 &#45; 通过 &#45;端 VS 包图](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")  
通过并行 VSPackage 安装程序  
  
 每个安装程序还包括两个安装程序之间共享的代码。 如果到常见位置安装共享的代码，则安装这两个.msi 文件将仅一次安装共享的代码。 第二个安装程序只需递增引用计数在组件上。 引用计数可确保 Vspackage 之一则在卸载，共享的代码将保持为其他的 VSPackage。 如果第二个 VSPackage 以及卸载，将删除共享的代码。  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>方案 4： 并排显示 VSPackage 更新  
 在此方案中，为你的 VSPackage[!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)]遇到从安全漏洞和你需要发出更新。 如下所示方案 2 中，你可以创建更新现有安装包括安全修复程序，以及部署与已在位置的安全修补程序的新安装的新.msi 文件。  
  
 在这种情况下，VSPackage 是安装在全局程序集缓存 (GAC) 中托管的 VSPackage。 当你重新生成使之包括安全修补程序时，必须更改程序集版本号的修订号部分。 注册信息的新的程序集版本号将覆盖以前的版本，导致[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载固定的程序集。  
  
 ![VS 端 &#45; 通过 &#45;端 VS 包更新图形](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")  
通过并行 VSPackage 更新安装程序  
  
 **请注意**通过并行程序集部署的详细信息，请参阅[简化部署和使用.NET Framework 解决 DLL 灾难](http://msdn.microsoft.com/library/ms973843.aspx)。  
  
## <a name="see-also"></a>另请参阅  
 [Windows 安装程序](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [支持多个版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)