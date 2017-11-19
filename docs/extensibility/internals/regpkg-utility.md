---
title: "RegPkg 实用工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ca3c5d5177b7f7e865f7fffb1bcd87a78d2e8cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="regpkg-utility"></a>RegPkg 实用工具
> [!NOTE]
>  在 Visual Studio 中注册包的首选的方法是使用.pkgdef 文件。 这使得扩展部署而无需访问系统注册表中，这是有关 VSIX 部署要求。 通过使用创建 Pkgdef 文件[CreatePkgDef 实用工具](../../extensibility/internals/createpkgdef-utility.md)。 Visual Studio 包部署的详细信息，请参阅[传送 Visual Studio 扩展](../../extensibility/shipping-visual-studio-extensions.md)。  
  
 RegPkg.exe 实用程序注册与 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，使其准备部署。 此实用程序是在后台 VSPackage 开发期间使用的。 它作为生成过程的一部分运行，以便你可以生成并在实验性配置单元中运行 VSPackage。  
  
 RegPkg 可以以几种格式生成系统注册表脚本。 你可以集成在部署项目，例如.msi 项目或 Windows Installer XML 工具集文件中的这些脚本。  
  
 RegPkg.exe 位于通常\< *Visual Studio SDK 安装路径*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe。 RegPkg 使用以下语法：  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 执行在指定的注册  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根。  
  
 /regfile:FileName  
 创建的.reg 文件，而不是更新注册表。  不能与 /vrgfile 或 /rgsfile 或 /wixfile 使用。  
  
 /rgsfile:FileName  
 创建.rgs file，而不是更新注册表。  不能与 /vrgfile 或 /regfile 或 /wixfile 使用。  
  
 /vrgfile:FileName  
 创建.vrg 文件，而不是更新注册表。  不能与 /regfile 或 /rgsfile 或 /wixfile 使用。  
  
 /rgm  
 创建.rgm 文件除了 rgs 文件。  必须与 /rgsfile 结合。  
  
 /wixfile:FileName  
 创建与 Windows Installer XML 工具集兼容的文件，而不是更新注册表。  不能与 /regfile 或 /rgsfile 或 /vrgfile 使用。  
  
 /codebase  
 使用基本代码，而不是程序集强制注册。  
  
 /assembly  
 使用程序集，而不是基本代码的强制注册。  
  
 / 注销  
 注销此包。  不能使用  
  
 与 /regfile 或 /vrgfile 或 /rgsfile 或 /wixfile。  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 [对 RegPkg 包注册进行故障排除](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)