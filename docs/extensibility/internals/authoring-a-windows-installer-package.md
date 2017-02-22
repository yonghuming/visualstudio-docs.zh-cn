---
title: "创作 Windows Installer 包 | Microsoft Docs"
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
  - "Vspackage 的.msi 文件"
  - "Vspackage 的 msi 文件"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 创作 Windows Installer 包
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

数据驱动的 Windows Installer 模型。 而不是编写一个过程的脚本，以将文件复制并写入注册表项，例如，您创作的行和包含文件和注册表数据的数据库表中的列。  
  
## 数据库项  
 若要安装 VSPackage 时，Windows Installer 包必须包含数据库条目，以执行以下任务:  
  
-   若要查找的版本的系统中搜索 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 你的 VSPackage 支持 \(使用包含 AppSearch、 CompLocator、 RegLocator、 DrLocator 和签名的 Windows Installer 表\)。  
  
-   如果没有支持的版本，则取消安装 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 安装或如果不满足的 VSPackage 的另一项系统要求 \(使用 LaunchCondition 表\)。  
  
-   安装 VSPackage 和相关文件 \(使用 directory、 组件和文件表\)。  
  
-   将相应信息来 VSPackage 添加到注册表 \(使用注册表表\)。  
  
-   集成 VSPackage 中的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 通过调用 **devenv.exe \/setup** \(使用 CustomAction 表\)。  
  
 有关详细信息，请参阅 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)。  
  
## 安装程序工具  
 各种第三方安装程序工具提供了 Windows Installer 程序包的开发环境。 两个免费工具如下所示:  
  
-   InstallShield Limited Edition  
  
     可以通过 Visual Studio 获取 InstallShield 的限定的版 **新项目** 对话框。 展开 **其他项目类型** ，然后选择 **安装和部署**。 选择 InstallShield 模板。  
  
-   Windows Installer XML 工具集  
  
     该工具集生成 Windows Installer 包从 XML 源文件。 该工具集是 Microsoft 的开源项目。 您可以下载源代码和可执行文件 [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix)。  
  
 对于将集成到商业产品 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], ，请参阅 [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/)。  
  
## 请参阅  
 [使用 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)