---
title: "支持多个版本的 Visual Studio |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc9c13ecf6a5cc6e62caa897adce16830026261a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>支持多个版本的 Visual Studio
术语*并排显示*意味着你可以安装和维护的同一台计算机上的产品的多个版本。 对于 Vspackage，这意味着用户可以安装在同一台计算机上的多个 Visual Studio 版本。 但是，不能具有并排显示的你的 Vspackage 加载到单个版本的 Visual Studio 的版本。  
  
 在你的 VSPackage 能够加载到 Visual Studio 的并行版本之前，考虑以下方面：  
  
-   你必须确定你想要遵照哪些并排显示实现策略。  
  
     有关详细信息，请参阅[选择之间共享和版本控制的 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。  
  
-   你的解决方案和项目文件格式必须符合你实现的策略。  
  
     有关详细信息，请参阅[升级自定义项目](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)和[注册的文件扩展名的并行部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   安装程序必须处理你实现的策略，以便已进行版本管理的组件，以及在所有版本间共享的组件已正确安装并注册。  
  
     有关详细信息，请参阅[与 Windows Installer 安装 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)以及[组件管理](../extensibility/internals/component-management.md)。  
  
    > [!NOTE]
    >  安装了版本的 Visual Studio 也会安装相应版本的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 例如，在同一台计算机上安装 Visual Studio 2010 和 Visual Studio 2012 还将安装的版本 4.0 和 4.5[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]分别。  
  
## <a name="in-this-section"></a>本节内容  
 [选择共享的 VSPackage 或带有版本的 VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 说明如何解决你的 VSPackage 中的并排显示问题。  
  
 [注册并行部署的文件扩展名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 描述你的 VSPackage 如何在通过并行方案中注册的文件关联。  
  
## <a name="related-sections"></a>相关章节  
 [使用 Windows Installer 安装 VSPackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
