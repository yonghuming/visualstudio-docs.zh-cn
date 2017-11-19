---
title: "为 VSPackage 选择的安装目录 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3462104e100ab672373f30dcd8228bc064746f2d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>为 VSPackage 选择的安装目录
VSPackage 和及其支持文件必须是用户的文件系统上。 位置取决于是否 VSPackage 托管或非托管，你的并行版本控制方案，并用户选择。  
  
## <a name="unmanaged-vspackages"></a>非托管的 Vspackage  
 非托管的 VSPackage 是可以安装在任何位置中的 COM 服务器。 其注册信息必须准确地反映其位置。 安装程序用户界面 (UI) 应提供作为子目录的找到 Windows Installer 属性的默认位置。 例如:   
  
 [找到]MyCompany\MyVSPackageProduct\V1.0\  
  
 应允许用户更改以适应保持小启动分区的用户的默认目录，并且希望在另一个卷上安装应用程序和工具。  
  
 如果你并排显示的方案使用版本控制的 VSPackage，你可以使用子目录来存储不同的版本。 例如:   
  
 [找到]MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [找到]MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [找到]MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>托管的 VSPackage  
 也可以在任何位置安装托管的 Vspackage。 但是，你应该考虑始终将它们安装到全局程序集缓存 (GAC) 以减少程序集加载时间。 托管的 Vspackage 始终是强名称的程序集，因为在 GAC 中安装它们意味着仅在安装时，使用其强名称签名验证。 安装在其他位置的文件系统的具有强名称的程序集必须具有每次加载时验证其签名。 当安装在 GAC 中的托管的 Vspackage 时，使用 regpkg 工具的**/assembly**交换机来编写指向程序集的强名称的注册表条目。  
  
 如果安装在 GAC 以外的位置中托管的 Vspackage，请按照针对非托管 Vspackage 给定选择目录层次结构的早期建议。 使用 regpkg 工具**/codebase**交换机来编写指向 VSPackage 程序集的路径的注册表条目。  
  
 有关详细信息，请参阅[注册和注销 Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="satellite-dlls"></a>附属 Dll  
 按照约定，VSPackage 附属 Dll，其中包含特定的区域设置的资源-位于 VSPackage 目录的子目录中。 子目录对应于区域设置 ID (LCID) 值。  
  
 [管理 Vspackage](../../extensibility/managing-vspackages.md)指示注册表项控制在何处[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]查找 VSPackage 的实际附属 DLL。 但是，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]尝试加载附属 DLL 的子目录名为的 LCID 值，按以下顺序：  
  
1.  默认 LCID (VS LCID 例如 \1033 为英语)  
  
2.  默认情况下 LCID 默认子语言。  
  
3.  系统默认 LCID。  
  
4.  与默认子语言的系统默认 LCID。  
  
5.  美国英语 (。 \1033 或。 \0x409)。  
  
 如果你的 VSPackage DLL 包含资源和 SatelliteDll\DllName 注册表条目指向它，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]尝试将它们加载的上述顺序。  
  
## <a name="see-also"></a>另请参阅  
 [选择共享并设置其版本 Vspackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [托管的包注册](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)