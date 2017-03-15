---
title: "VSPackage 注册 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
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
ms.openlocfilehash: bebd023d8cbecf97f75570bf57ed2cd4462ffe92
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-registration"></a>VSPackage 注册
必须告知 VSPackages[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]他们安装，并且应进行加载。 通过在注册表中写入信息来完成此过程。 这是安装程序的典型的作业。  
  
> [!NOTE]
>  已接受的做法是在 VSPackage 开发使用自我注册过程中。 但是，[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]合作伙伴，无法提供作为安装的一部分使用自我注册他们的产品。  
  
 在 Windows 安装程序包的注册表项通常都注册表表中。 此外可以在注册表表中注册的文件扩展名。 但是，Windows Installer 提供程序标识符 (ProgId)、 类、 extension 和谓词表通过内置支持。 有关详细信息，请参阅[数据库表](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)。  
  
 请确保注册表项适合于您选择通过并行策略的组件相关联。 例如，共享文件的注册表项应与该文件的 Windows 安装程序组件相关联。 同样，特定于版本的文件的注册表项应与该文件的组件相关联。 否则为安装或卸载你的 VSPackage 的某个版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可能在其他版本中会中断你的 VSPackage。 有关详细信息，请参阅[支持多个版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  管理注册的最简单方法是对开发人员注册和安装时间登记在同一个文件中使用相同的数据。 例如，某些安装程序开发工具可以在生成时使用.reg 格式文件中。 如果开发人员维护其自己的日常开发的.reg 文件并调试时，这些文件可以包含在安装程序自动。 如果您不能自动共享注册数据，必须确保注册数据的安装程序的副本是最新。  
  
## <a name="registering-unmanaged-vspackages"></a>注册非托管的 VSPackages  
 非托管的 VSPackages （包括由 Visual Studio 包模板生成的） 使用 ATL 样式.rgs 文件来存储注册信息。 特定于 ATL.rgs 文件格式，通常不能用作-通过创作工具的安装。 必须单独维护的 VSPackage 安装程序的注册信息。 例如，开发人员可以将文件保存在.reg 格式与.rgs 同步文件更改。 可以为开发工作与 RegEdit 合并或由安装程序的.reg 文件。  
  
## <a name="registering-managed-vspackages"></a>注册托管的 VSPackages  
 RegPkg 工具从托管 VSPackage 读取注册属性，并可以是信息直接写入注册表或可供安装程序的写入.reg 格式文件。  
  
> [!NOTE]
>  RegPkg 工具不是可再发行组件，并不能用于注册用户的系统上的 VSPackage。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>为什么 Vspackage 不应自行注册在安装时  
 VSPackage 安装程序不应依赖自注册。 从表面看，仅在 VSPackage 本身中保留的 VSPackage 注册表值看起来是个好主意。 在给定其日常工作的开发人员需要可用的注册表值和测试，最好避免维护在安装程序中的注册表数据的单独副本。 安装程序可以依赖 VSPackage 本身写入注册表值。  
  
 虽然在理论上适用，自行注册有几个缺点，使其适合 VSPackage 安装︰  
  
-   正确支持安装、 卸载、 安装回滚和卸载回滚要求您创作的自注册通过调用 RegPkg 每个托管 VSPackage 的四个自定义操作。  
  
-   通过并行支持 č ø 方法可能需要您编写的每个受支持的版本调用 RegSvr32 或 RegPkg 的四个自定义操作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   不能安全地回滚安装具有自行注册模块，因为没有没有办法得知自行注册的密钥由另一个功能或应用程序。  
  
-   有时，自行注册的 Dll 将链接到辅助 Dll 中不存在或版本有错误。 与此相反，Windows 安装程序可以注册 Dll 使用此注册表表而不依赖于系统的当前状态。  
  
-   访问网络资源，如类型库中，如果组件是同时指定为从源运行和 SelfReg 表中列出，则可以拒绝自注册代码。 这会导致要在管理安装过程中失败的组件安装。  
  
## <a name="see-also"></a>另请参阅  
 [Windows 安装程序](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [托管的程序包注册](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
