---
title: "使用 Windows Installer 安装 Vspackage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5061a52de32f699bbe234f729bb4f852ee966933
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="installing-vspackages-with-windows-installer"></a>使用 Windows Installer 安装 Vspackage
将集成到你的 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]需要多个只需将文件复制到用户的计算机。 你的 VSPackage 的安装程序必须安装 VSPackage 和其依赖的文件，并注册并将它们到集成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 你的 VSPackage 可以利用集成功能，例如在上显示一个图标[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]初始屏幕和有关对话框。  
  
 Microsoft Windows Installer 文件是分发你的 Vspackage 的推荐的方式。 能够轻松使用 Windows Installer 程序包可以在支持的任何 Windows 操作系统上运行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅[Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)。  
  
## <a name="in-this-section"></a>本节内容  
 [Windows Installer 基本知识](../../extensibility/internals/windows-installer-basics.md)  
 提供 Windows 安装程序的概述。  
  
 [VSPackage 安装方案](../../extensibility/internals/vspackage-setup-scenarios.md)  
 讨论可支持通过并行安装的这两种你的 Vspackage 的不同方法和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [创作 Windows Installer 程序包](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 提供的安装程序遵循正确安装和将其集成到 Vspackage 的典型步骤概述[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [检测系统要求](../../extensibility/internals/detecting-system-requirements.md)  
 描述如何安装程序可以检测[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，如果未满足 VSPackage 要求，其组件和取消将安装程序。  
  
 [组件管理](../../extensibility/internals/component-management.md)  
 讨论如何开发的安装程序将保留以前的产品版本的完整性。  
  
 [为 VSPackage 选择安装目录](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 总结了查找 Vspackage 的选项。  
  
 [VSPackage 注册](../../extensibility/internals/vspackage-registration.md)  
 讨论如何在安装时注册 Vspackage 并自注册的原因是个好主意。  
  
 [部署项目类型](../../extensibility/internals/deploying-project-types.md)  
 讨论如何为托管代码的项目类型中使用新的项目类型聚合器。  
  
 [如何：生成安装程序的注册表信息](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 说明如何使用 RegPkg.exe 为托管的 VSPackage 生成注册清单。  
  
 [安装后必须运行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 说明如何运行安装后命令集成到 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [使用 Windows Installer 卸载 VSPackage](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 描述用户卸载你的 VSPackage 时，安装程序，必须执行的步骤。  