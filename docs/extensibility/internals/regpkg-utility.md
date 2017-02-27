---
title: "RegPkg 实用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regpkg，注册实用程序"
  - "注册、 regpkg 实用程序"
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# RegPkg 实用程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  在 Visual Studio 中注册包的首选的方式是使用.pkgdef 文件。 这样可以扩展部署而无需访问系统注册表中，这是 VSIX 部署的要求。 通过使用创建 Pkgdef 文件 [CreatePkgDef 实用程序](../../extensibility/internals/createpkgdef-utility.md)。 Visual Studio 包部署的详细信息，请参阅 [传送 Visual Studio 扩展](../../extensibility/shipping-visual-studio-extensions.md)。  
  
 RegPkg.exe 实用程序注册与 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 并准备进行部署。 在 VSPackage 开发过程中在后台使用此实用程序。 它作为生成过程的一部分运行，以便您可以生成并运行试验性的配置单元中的 VSPackage。  
  
 RegPkg 可以用多种格式生成系统注册表脚本。 您可以将合并这些脚本在部署项目，如.msi 项目或 Windows Installer XML 工具集文件中。  
  
 RegPkg.exe 是通常位于 \<*Visual Studio SDK 安装路径*\> \\VisualStudioIntegration\\Tools\\Bin\\RegPkg.exe。 RegPkg 使用以下语法:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 \/root:root  
 执行下指定的注册  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根。  
  
 \/regfile:FileName  
 创建.reg 文件，而不是更新注册表。  不能与 \/vrgfile 或 \/rgsfile 或 \/wixfile 使用。  
  
 \/rgsfile:FileName  
 创建.rgs 文件，而不是更新注册表。  不能与 \/vrgfile 或 \/regfile 或 \/wixfile 使用。  
  
 \/vrgfile:FileName  
 创建.vrg 文件，而不是更新注册表。  不能与 \/regfile 或 \/rgsfile 或 \/wixfile 使用。  
  
 \/rgm  
 创建一个.rgm 文件除了 rgs 文件。  必须与 \/rgsfile 结合。  
  
 \/wixfile:FileName  
 创建 Windows Installer XML 工具集兼容的文件，而不是更新注册表。  不能与 \/regfile 或 \/rgsfile 或 \/vrgfile 使用。  
  
 \/codebase  
 使用基本代码，而不是程序集强制注册。  
  
 \/assembly  
 向程序集，而不是基本代码的强制注册。  
  
 \/ 注销  
 注销此包。  不能使用  
  
 与 \/regfile 或 \/vrgfile 或 \/rgsfile 或 \/wixfile。  
  
## 请参阅  
 [发布产品](../../misc/releasing-a-visual-studio-integration-product.md)   
 [疑难解答 RegPkg 包注册](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)