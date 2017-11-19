---
title: "共享和版本控制 Vspackage 之间进行选择 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9442d6685d27a9270c1e71e3a79e9f810b6f40f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>选择共享并设置其版本 Vspackage
不同版本的 Visual Studio 可以在同一台计算机上共存。 Vspackage 可以支持的任何组合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本。  
  
 你可以启用通过并行安装的 Vspackage 通过两种策略、 共享的策略或版本控制的策略。 同时容纳多个版本的存在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和关联的版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
 在共享的策略中，一个 VSPackage 注册为中的多个版本的使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在版本控制的策略中，安装了多个 VSPackage Dll，一个用于每个版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]你支持的。  
  
## <a name="shared-vspackages"></a>共享的 Vspackage  
 当你使用相同的 VSPackage 中的多个版本使用共享的 VSPackage 适合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 若要实现共享的 VSPackage，你必须执行以下步骤：  
  
-   使你的 VSPackage 的多个版本与兼容[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 所以，这样做的两种方法都可用于：  
  
    -   限制你与使用仅的最早版本的功能的 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]你支持的。  
  
    -   程序调整到的版本，以适应你的 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]正在其中运行。 然后，如果较新的服务的查询失败，你的 VSPackage 可以提供其他服务中支持的较旧版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   适当地注册你的 VSPackage。 有关详细信息，请参阅[VSPackage 注册](../extensibility/internals/vspackage-registration.md)和[托管 VSPackage 注册](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)。  
  
-   适当地注册文件扩展名。 有关详细信息，请参阅[注册的文件扩展名的并行部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   创建将部署你的 VSPackage 的适当版本的安装程序[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅[与 Windows Installer 安装 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)和[组件管理](../extensibility/internals/component-management.md)。  
  
-   解决注册冲突的问题。 有关详细信息，请参阅[VSPackage 注册](../extensibility/internals/vspackage-registration.md)。  
  
-   确保共享和版本控制文件采用引用计数来允许安全的安装和删除多个版本。 有关详细信息，请参阅[组件管理](../extensibility/internals/component-management.md)。  
  
## <a name="versioned-vspackages"></a>版本控制的 Vspackage  
 在版本控制的 VSPackage 策略下, 创建的每个版本的一个 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]你支持的。 当你需要充分利用所提供的更高版本的服务执行此操作适合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，因为每个 VSPackage 可以演化而不影响其他。 不过，从的单个基本代码或从多个基本的独立代码，请创建多个二进制文件的版本控制策略，可能需要更多的初始开发比共享策略。 此外，其他设置工作可能因为你必须创建单独的安装每个版本，或者一个安装程序检测到的版本要求[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安装，以及你的 VSPackage 支持。  
  
## <a name="binary-compatibility"></a>二进制兼容性  
 通常情况下，二进制兼容性使开发与早期版本的 Visual Studio 运行更高版本的 Visual Studio 中的本机代码 Vspackage。 但是，有三个重要的例外情况：  
  
-   如果你的 VSPackage 依赖于特定版本的公共语言运行时，则它必须确定哪一个版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]它正在运行。  
  
-   VSPackage 可能会对另一个 VSPackage 或其他产品的特定功能依赖关系。 因此，VSPackage 可以运行仅其中满足其依赖关系。  
  
-   VSPackage 可能会影响在安全修补程序[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]service pack 或更高版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在这些情况下，VSPackage 开发使用早期版本的[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]可能无法运行它的版本中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]应用的安全修补程序后。 但是，你可以重新生成较新版本包并将其还在早期版本中运行。  
  
 必须使用的版本生成托管的 Vspackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]匹配的目标版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 除了为 VSPackage 二进制文件的位置规划二进制兼容性，你还应考虑解决方案和项目文件格式。 如果你的 VSPackage 创建一个新的项目类型，则必须确定它是否可以运行一个版本中还是在多个版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅[升级自定义项目](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Windows Installer 安装 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [组件管理](../extensibility/internals/component-management.md)