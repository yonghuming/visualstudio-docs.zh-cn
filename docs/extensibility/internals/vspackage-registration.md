---
title: "VSPackage 注册 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 263e2adf69aa479974a07dbb2acc2d4cd8f2a0dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vspackage-registration"></a>VSPackage 注册
Vspackage 必须告知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它们安装，应将加载。 此过程通过在注册表中写入信息。 这是典型的作业的安装程序。  
  
> [!NOTE]
>  接受的做法是在 VSPackage 开发使用自助注册过程。 但是，[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]合作伙伴，无法提供作为安装的一部分使用自助注册他们的产品。  
  
 Windows Installer 包中的注册表项通常都在注册表表。 此外可以在注册表表中注册的文件扩展名。 但是，Windows Installer 提供内置支持通过编程标识符 (ProgId)、 类、 扩展，和谓词表。 有关详细信息，请参阅[数据库表](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)。  
  
 请确保你注册表条目是与适用于你选择通过并行策略该组件关联。 例如，共享的文件的注册表项应与该文件的 Windows Installer 组件相关联。 同样，特定于版本的文件的注册表条目应与该文件的组件相关联。 否则为安装或卸载你的 VSPackage 的某个版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]其他版本中可能会中断你的 VSPackage。 有关详细信息，请参阅[支持多个 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  管理注册的最简单方法是在同一文件中使用相同的数据，开发人员注册和安装时注册。 例如，某些安装程序开发工具可以在生成时使用.reg 格式文件中。 如果开发人员维护日常开发的.reg 文件和调试，这些相同的文件可以包含在安装程序自动。 如果你不能自动共享注册数据，则必须确保安装程序的注册数据副本是最新。  
  
## <a name="registering-unmanaged-vspackages"></a>注册非托管的 Vspackage  
 （包括那些由 Visual Studio 包模板生成） 的非托管的 Vspackage 使用 ATL 样式.rgs 文件来存储注册信息。 .Rgs 文件格式是特定于 ATL，通常不能用作-是由创作工具的安装。 必须单独维护 VSPackage 安装程序的注册信息。 例如，开发人员可以将文件存储在.reg 格式与.rgs 同步文件更改。 可以与 RegEdit 合并对于的开发工作或由安装程序的.reg 文件。  
  
## <a name="registering-managed-vspackages"></a>注册托管的 Vspackage  
 RegPkg 工具读取从托管的 VSPackage 的注册属性和可以是信息直接写入注册表或可供安装程序的写.reg 格式文件。  
  
> [!NOTE]
>  RegPkg 工具不是可再发行组件，并不能用于注册用户的系统上 VSPackage。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>为什么 Vspackage 应不自行注册在安装时  
 VSPackage 安装程序不应依赖于自注册。 从表面看，在 VSPackage 本身中仅保留 VSPackage 的注册表值似乎是一个不错的主意。 给定开发人员需要进行日常工作提供的注册表值和测试，因此最好避免维护在安装程序的注册表数据的单独副本。 安装程序可以依赖于 VSPackage 本身可以写入注册表值。  
  
 在理论上良好，同时自助注册还提供使其适合 VSPackage 安装的几个缺点：  
  
-   正确支持安装、 卸载、 安装回滚和卸载回滚，需要创作通过调用 RegPkg 自助注册每个托管 vspackage 的四个自定义操作。  
  
-   通过并行支持你方法可能需要你创作的每个受支持版本的调用 RegSvr32 或 RegPkg 的四个自定义操作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   不能安全地回滚安装具有自行注册的模块，因为没有指明如果由另一个功能或应用程序使用自行注册的密钥的方法。  
  
-   有时，自行注册的 Dll 将链接到辅助 Dll 不存在或版本错误。 与此相反，Windows Installer 可以注册使用此注册表表而不依赖于系统的当前状态的 Dll。  
  
-   可能被拒绝自注册代码，访问网络资源，如类型库，如果组件是同时指定为运行从源和 SelfReg 表中列出。 这会导致要管理的安装过程中发生故障的组件安装。  
  
## <a name="see-also"></a>另请参阅  
 [Windows 安装程序](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [托管的包注册](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)