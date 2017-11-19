---
title: "组件管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a3100252dd5ddfcebd791588a4041c8d588e8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="component-management"></a>组件管理
在 Windows 安装程序中的任务的单位称为 （有时称为 WICs 或只是组件） 的 Windows 安装程序组件。 一个 GUID 标识每个 WIC，这是安装和引用计数使用 Windows Installer 的设置的基本单位。  
  
 尽管有好几种产品可用于创建 VSPackage 安装程序，但此讨论将假定使用 Windows Installer (.msi) 文件。 在创建时到安装程序，必须正确管理文件部署，以便正确引用计数在所有时间发生。 因此，你产品的不同版本将不干扰或中断相互中多种安装和卸载方案。  
  
 在 Windows 安装程序中，引用计数会发生在组件级别。 你必须仔细组织资源-文件、 注册表项等-为组件。 有其他级别的组织-如模块、 功能和产品-可帮助在不同的方案。 有关详细信息，请参阅[Windows 安装程序基础知识](../../extensibility/internals/windows-installer-basics.md)。  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>创作通过并行安装的安装程序的指导原则  
  
-   作者文件并为其自己的组件版本之间共享的注册表项。  
  
     这允许您轻松下一版本中使用它们。 例如，全局，注册的类型库的文件扩展名，在注册表中，依次类推中注册其他项。  
  
-   分组到单独的合并模块的共享的组件。  
  
     这有助于作者正确以通过并行向前移动。  
  
-   跨版本使用相同的 Windows Installer 组件安装共享的文件和注册表项。  
  
     如果你使用不同的组件，则将卸载文件和注册表项时卸载一个版本控制的 VSPackage，但仍安装另一个 VSPackage。  
  
-   不要混合在同一组件的版本控制和共享项。  
  
     这样使得无法安装到全局位置和版本控制项独立的位置的共享的项。  
  
-   没有指向版本控制的文件的共享的注册表项。  
  
     如果这样做，在安装另一个版本控制 VSPackage 时，将覆盖的共享的密钥。 删除第二个版本后，密钥指向文件将消失。  
  
## <a name="see-also"></a>另请参阅  
 [选择共享并设置其版本 Vspackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage 安装方案](../../extensibility/internals/vspackage-setup-scenarios.md)