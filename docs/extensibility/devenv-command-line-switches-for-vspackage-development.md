---
title: "Devenv 命令行开关，VSPackage 开发 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca93d63236eb1b50663eff4c86a6ae3603600802
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>有关 VSPackage 开发 Devenv 命令行开关
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]允许开发人员执行 devenv.exe，启动 Visual Studio 集成的开发环境 (IDE) 的文件时自动执行从命令行的任务。  
  
 涉及以下任务：  
  
-   预先设计在 IDE 外部配置中部署应用程序。  
  
-   自动使用预设的生成项目的生成设置，或调试配置。  
  
-   在 IDE 之外所有从加载在特定配置中，IDE。 此外，你可以自定义启动时 IDE。  
  
## <a name="guidelines-for-switches"></a>交换机的准则  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文档介绍了用户级 devenv 命令行开关。 有关详细信息，请参阅[Devenv 命令行开关](../ide/reference/devenv-command-line-switches.md)。 Devenv 还支持其他命令行开关可用于 VSPackage 开发、 部署和调试。  
  
|命令行开关|描述|  
|--------------------------|-----------------|  
|/safemode|将启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式下，加载默认 IDE 和服务。 /Safemode 开关加载时阻止所有第三方 Vspackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]启动，从而确保稳定的执行。<br /><br /> 此开关不带参数。|  
|/resetskippkgs|清除所有跳过加载选项已添加的用户都想要避免加载有问题的 Vspackage，然后启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 SkipLoading 标记存在禁用加载的 VSPackage。 清除标记将重新启用加载的 VSPackage。<br /><br /> 此开关不带参数。|  
|/rootsuffix|启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用备用位置。 以下命令运行由快捷方式创建的[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]安装程序：<br /><br /> devenv /RootSuffix exp<br /><br /> 在这种情况下，exp 标识与特定的后缀，例如 10.0Exp 而不是 10.0 的位置。 实验实例，可调试分开的实例 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]你用于编写代码。<br /><br /> 此开关可以接受任何字符串，标识使用 VSRegEx.exe 创建的位置。 有关详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。|  
|/splash|显示[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]照常初始屏幕，然后在显示于主 IDE 之前显示一个消息框。 消息框中，可以研究初始屏幕，以检查 VSPackage 产品图标，如。<br /><br /> 此开关不带参数。|  
  
## <a name="see-also"></a>另请参阅  
 [添加命令行开关](../extensibility/adding-command-line-switches.md)   
 [Devenv 命令行开关](../ide/reference/devenv-command-line-switches.md)