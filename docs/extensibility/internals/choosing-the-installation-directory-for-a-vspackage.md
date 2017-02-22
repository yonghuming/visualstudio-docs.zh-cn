---
title: "为 VSPackage 选择的安装目录 | Microsoft Docs"
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
  - "Vspackage，安装目录"
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 为 VSPackage 选择的安装目录
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 及其支持的文件必须在用户文件系统。  位置取决于 VSPackage 是托管或非托管的，该并行版本控制的模式和用户选择。  
  
## 非托管 Vspackage  
 非托管 VSPackage 是可以位于任何位置安装的 COM 服务器。  其注册信息需要准确反映其位置。  安装程序用户 \(UI\)界面应提供默认位置为 ProgramFilesFolder Windows Installer 属性的子目录。  例如：  
  
 \[programfilesfolder\] 后 MyCompany \\MyVSPackageProduct\\V 1.0 \\  
  
 用户应该允许更改默认内容适应在另一个数保留一个小型新兴分区并希望安装应用程序和工具的用户。  
  
 如果该并行模式使用的 VSPackage，可以使用子目录存储不同版本。  例如：  
  
 \[programfilesfolder\] 后 MyCompany \\MyVSPackageProduct\\V 1.0 \\ 2002 \\  
  
 \[programfilesfolder\] 后 MyCompany \\MyVSPackageProduct\\V 1.0 \\ 2003 \\  
  
 \[programfilesfolder\] 后 MyCompany \\MyVSPackageProduct\\V 1.0 \\ 2005 \\  
  
## 托管 Vspackage  
 托管 Vspackage 可在任何位置也会安装。  但是，您应考虑始终会安装到全局程序集缓存 \(GAC\)减少程序集加载时。  由于托管 Vspackage 始终具有强名称程序集，它们安装在 GAC 意味着它们的强名称签名验证是否只接受在安装时。  ，在加载后，在文件系统中的其他位置安装的强名称程序集必须具有自己的签名进行验证。  在 GAC 中安装托管的 Vspackage，请使用 regpkg 工具的 **\/assembly** 开关编写指向程序集的强名称的注册表项。  
  
 除了 GAC 外，如果在位置安装托管的 Vspackage，请遵循为选择的目录层次结构非托管 Vspackage 给定的反斜更早的建议。  使用 regpkg 工具的 **\/codebase** 开关编写指向 VSPackage 程序集的路径的注册表项。  
  
 有关更多信息，请参见 [注册和注销 VSPackages 迁移](../../extensibility/registering-and-unregistering-vspackages.md)。  
  
## 附属 DLL  
 按照约定， VSPackage —包含特定的资源文件 —的附属 DLL 位于 VSPackage 目录的子目录。  子目录对应于区域设置 ID \(lcid\) 值。  
  
 [管理 Vspackage](../../extensibility/managing-vspackages.md) 指示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 实际上查找 VSPackage 的附属 DLL 中的该注册表项控件。  但是， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在对于 LCID 值名为的子目录尝试加载附属 DLL，按以下顺序:  
  
1.  默认 LCID \(带 LCID 例如 \\1033 for English\)  
  
2.  使用默认子语言的默认 LCID。  
  
3.  系统默认 LCID。  
  
4.  使用默认子语言的系统默认 LCID。  
  
5.  美式  英语 \(。  \\ 1033 或。  \\ 0x409\)。  
  
 如果 VSPackage DLL 包含资源，并 SatelliteDll \\DllName 注册表的入口点。它， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 尝试按上面的顺序加载。  
  
## 请参阅  
 [共享和版本控制的 Vspackage 之间进行选择](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [Managed Package Registration](http://msdn.microsoft.com/zh-cn/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)