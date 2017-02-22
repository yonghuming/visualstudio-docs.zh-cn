---
title: "VSPackage 安装方案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage，部署注意事项"
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# VSPackage 安装方案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

请务必设计 VSPackage 安装程序的灵活性。 例如，你可能需要在将来，释放安全修补程序或可能更改的业务策略，需要全面的并行版本控制支持。  
  
 在 [支持多个版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), ，你可以阅读的优点和支持的并行安装问题 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 与你的 VSPackage 的共享或通过并行安装。 简单地说，通过并行 VSPackages 迁移为您提供最大的灵活性以支持新功能的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 本主题中讨论的方案不是唯一的选择，但它们所列举的为建议的最佳方法。  
  
## 组件、 隐私和共享  
  
##### 使您的组件独立  
 一旦确定，并填充一个组件，请分配 `GUID`, ，并将组件部署，则不能更改其构成。 如果未更改组件的组合，生成的组件必须具有一个新的新组件 `GUID`。 给定这些事实，通过使每个组件独立的独立单元能够提供最大版本控制的灵活性。 有关控制组件的规则的详细信息，请参阅 [更改组件代码](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) 和 [出现什么情况组件规则被破坏？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)。  
  
##### 不混用在组件中的共享和专用资源  
 在组件级别上发生的引用计数。 因此，混合使用一个组件中的共享和专用资源会导致无法更新专用资源，如可执行文件，而不会还覆盖共享的资源。 这种情况下创建的向后兼容性问题，并会限制您只能从创建并行的功能。  
  
 例如，使用注册表值来注册与你的 VSPackage [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 应始终在组件中独立于用来注册与你的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 共享的文件或注册表值进入另一个组件。  
  
## 方案 1︰ 共享的 VSPackage  
 在此方案中，共享 VSPackage \(支持的多个版本的单一二进制文件 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\) 在 Windows 安装程序包中提供。 注册的每一个版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 受用户选择的功能。 它还意味着，当分配到单独的功能，每个组件可以选择单独的安装或卸载时，将用户放在 VSPackage 结合起来的不同版本的控件 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 \(请参阅 [Windows Installer 功能](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) 有关使用 Windows Installer 程序包中的功能的详细信息。\)  
  
 ![VS 共享 VS 包图](../../extensibility/internals/media/vs_sharedpackage.png "VS\_SharedPackage")  
共享的 VSPackage 安装  
  
 如图中所示，共享的组件都 Feat\_Common 功能，始终安装的一部分。 通过使 Feat\_VS2002 和 Feat\_VS2003 功能可见，用户可以选择在安装到哪个版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 他们希望 VSPackage 来集成。 用户还可以使用 Windows Installer 维护模式以添加或删除功能，在这种情况下添加或删除不同版本的 VSPackage 注册信息 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
> [!NOTE]
>  将一项功能的显示列设置为 0 会隐藏它。 低级别列值，如 1，可确保始终将被安装。 有关详细信息，请参阅 [INSTALLLEVEL 属性](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) 和 [功能表](http://msdn.microsoft.com/library/aa368585.aspx)。  
  
## 方案 2︰ 共享 VSPackage 更新  
 在此方案中，发运 VSPackage 安装方案 1 中的更新的版本。 为了便于讨论，此更新增加了对支持 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，但它也可以是一个更简单的安全修补程序或 bug 修复服务包。 安装较新的组件的 Windows 安装程序的规则要求已在系统上不变的组件不会被再次复制。 在这种情况下，对版本 1.0 已存在的系统将覆盖更新的组件 Comp\_MyVSPackage.dll，并使用户可以选择添加新功能 Feat\_VS2005 Comp\_VS2005\_Reg 与其组件。  
  
> [!CAUTION]
>  每当在的多个版本之间共享 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，很重要的 VSPackage 的后续版本，保持与以前版本的向后兼容性 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其中不能保持向后兼容，则必须使用通过并行、 专用的 Vspackage。 有关详细信息，请参阅[支持多个版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
 ![VS 共享 VS 包更新图像](../../extensibility/internals/media/vs_sharedpackageupdate.png "VS\_SharedPackageUpdate")  
共享 VSPackage 更新安装程序  
  
 此方案提供了一个新的 VSPackage 安装程序，充分利用 Windows Installer 支持次要升级。 用户只需在安装版本 1.1 和 1.0 版，它将升级。 但是，不需要具有系统上的版本 1.0。 相同的安装程序将没有 1.0 版的系统上安装 1.1 版。 能够以这种方式的次要升级升级的优点是不需要经历开发升级的安装程序和完整版产品安装程序的工作。 一个安装程序中执行这两项工作。 安全修补程序或服务包可能会改为利用 Windows Installer 修补程序。 有关详细信息，请参阅 [修补和升级](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)。  
  
## 方案 3︰ 通过并行 VSPackage  
 此方案提供了两个 VSPackage 安装 — 一个用于每个版本的 Visual Studio.NET 2003年和 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 每个安装程序会安装端并排或私有，VSPackage \(一个用于专门构建并为特定版本的安装 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\)。 每个 VSPackage 位于其自己的组件。 因此，每个可以单独服务与修补程序或维护释放。 由于 VSPackage DLL 现在是特定于版本，可安全地将其注册信息包括在与 DLL 相同的组件。  
  
 ![图：VS 并行 VS 包](../../extensibility/internals/media/vs_sbys_package.gif "VS\_SbyS\_Package")  
通过并行 VSPackage 安装程序  
  
 每个安装程序还包括两个安装程序之间共享的代码。 如果共享的代码安装到一个公共位置中，安装这两个.msi 文件将仅一次安装共享的代码。 第二个安装程序只是递增引用计数在组件上。 引用计数可以确保，如果卸载了其中一个 Vspackage，共享的代码将其他 VSPackage 保持。 如果同时卸载了第二个 VSPackage，将删除共享的代码。  
  
## 方案 4︰ 通过并行 VSPackage 更新  
 在此方案中，为你的 VSPackage [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] 之间发生从安全漏洞，您需要发出更新。 如下所示方案 2 中，您可以创建新的.msi 文件更新现有的安装来包括安全修复程序，以及部署新安装与已到位的安全修补程序。  
  
 在这种情况下，VSPackage 是安装在全局程序集缓存 \(GAC\) 中的托管的 VSPackage。 当您重新生成使之包括安全修补程序时，必须更改程序集版本号的修订号部分。 注册信息的新的程序集版本号会覆盖以前的版本，从而导致 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 加载固定的程序集。  
  
 ![图：VS 并行 VS 包更新](../../extensibility/internals/media/vs_sbys_packageupdate.png "VS\_SbyS\_PackageUpdate")  
通过并行 VSPackage 更新安装程序  
  
 **注意** 并行程序集部署的详细信息，请参阅 [简化部署和使用.NET Framework 解决 DLL Hell](http://msdn.microsoft.com/library/ms973843.aspx)。  
  
## 请参阅  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [支持多个版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)