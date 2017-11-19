---
title: "卸载使用 Windows Installer VSPackage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b71c977fcc616c6d9cf30b78c9fd7610f11bcd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>卸载使用 Windows Installer VSPackage
Windows Installer 大多数情况下，可以只需通过卸载你的 VSPackage"撤消"它未安装你的 VSPackage。 自定义操作中所述[命令，必须为运行后安装](../../extensibility/internals/commands-that-must-be-run-after-installation.md)必须也卸载后运行。 由于指向 devenv.exe 的调用发生在安装和卸载的情况下了 InstallFinalize 标准操作之前，所以 CustomAction 和 InstallExecuteSequence 表条目将用作这两种情况。  
  
> [!NOTE]
>  运行`devenv /setup`卸载 MSI 包后。  
  
 作为一般规则，如果将自定义操作添加到 Windows Installer 程序包，则必须处理这些操作期间卸载和回滚。 如果你添加自定义操作以便自行注册你的 VSPackage，例如，必须添加自定义操作以便太注销它。  
  
> [!NOTE]
>  它是用户可以安装你的 VSPackage，然后卸载版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]与它集成。 你可以帮助确保你的 VSPackage 的卸载工作在这种情况下通过消除在运行具有依赖项的代码的自定义操作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>在处理启动条件卸载时间  
 LaunchConditions 标准操作读取的行 LaunchCondition 表以显示错误。 如果不满足条件的消息。 当启动条件通常用于确保满足系统要求，则可以通常跳过启动条件在卸载过程通过添加条件， `NOT Installed`，到 LaunchCondition 表的 LaunchConditions 行。  
  
 一种替代方法是将添加`OR Installed`来启动卸载过程并不重要的条件。 这将确保该条件在卸载期间始终为 true，且因此不会显示启动条件错误消息。  
  
> [!NOTE]
>  `Installed`是 Windows Installer 设置在检测到你的 VSPackage，已安装在系统上的属性。  
  
## <a name="see-also"></a>另请参阅  
 [Windows 安装程序](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [检测系统要求](../../extensibility/internals/detecting-system-requirements.md)