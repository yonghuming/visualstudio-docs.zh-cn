---
title: "创作 Windows Installer 包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f646e2234adf0eb0117f154838b15d7b3aa200e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="authoring-a-windows-installer-package"></a>创作 Windows Installer 包
数据驱动器的 Windows Installer 模型。 而不是撰写的过程的脚本将文件复制和写入注册表项，例如，您创作行和包含文件和注册表数据的数据库表中的列。  
  
## <a name="database-entries"></a>数据库项  
 若要安装 VSPackage，Windows Installer 包必须包含数据库条目，执行以下任务：  
  
-   搜索系统后，若要查找的版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]你的 VSPackage 支持 （使用包括 AppSearch、 CompLocator、 RegLocator、 DrLocator 和签名的 Windows Installer 表）。  
  
-   取消安装，如果没有支持的版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]安装或如果未满足的 VSPackage 的另一个系统要求 （使用 LaunchCondition 表）。  
  
-   安装 VSPackage 和相关文件 （使用 directory、 组件和文件表）。  
  
-   将相应信息来 VSPackage 添加到注册表 （使用注册表表）。  
  
-   将集成在 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过调用**devenv.exe /setup** （使用 CustomAction 表）。  
  
 有关详细信息，请参阅[Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)。  
  
## <a name="setup-tools"></a>安装程序工具  
 不同的第三方安装程序工具，提供用于 Windows Installer 程序包的开发环境。 两个可用的工具如下所示：  
  
-   InstallShield Limited Edition  
  
     你可以通过 Visual Studio 获取 InstallShield 的受限的版本**新项目**对话框。 展开**其他项目类型**，然后选择**安装和部署**。 选择 InstallShield 模板。  
  
-   Windows Installer XML 工具集  
  
     工具集生成 XML 源文件中的 Windows Installer 程序包。 工具集，则 Microsoft 开放源代码项目。 你可以下载源代码和可执行文件从[http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix)。  
  
 用于将集成到的商业产品[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，请参阅[http://visualstudiogallery.com](http://visualstudiogallery.com/)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Windows Installer 安装 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)