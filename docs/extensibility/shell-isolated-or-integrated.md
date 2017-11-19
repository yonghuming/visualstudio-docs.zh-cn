---
redirect_url: shell/shell-isolated-or-integrated
title: "Shell （独立或集成） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f06af0b884d404b3fd2e8e36cac235c10d254bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell （独立或集成）
你可以创建自己的基于 Visual Studio 的应用程序集成或独立模式中。 在集成模式下，将除了你的应用程序可用许多 Visual Studio 功能。 在独立模式下，你可以选择要随自己的扩展一起分发的 Visual Studio 功能的子集。  
  
## <a name="integrated-mode"></a>集成模式下  
 集成模式下使用户能够使用标准 Visual Studio 功能以及自定义工具。 集成的外壳主要适用于托管编程语言和软件开发工具。  
  
 与任何其他版本的同一台计算机安装的 Visual Studio 合并自动生成在集成外壳程序上的自定义工具。 如果尚未安装 Visual Studio，你可以提供集成的 Visual Studio shell 的可再发行组件版本。  
  
 集成的 Visual Studio shell 的可再发行组件版本不包括编程语言和支持其各自的项目系统的功能。  
  
> [!NOTE]
>  Visual Studio shell 集成模式下可以与 Visual Studio 速成版除外的所有版本一起安装。  
  
 有关详细信息，请参阅[Visual Studio Shell （集成）](../extensibility/visual-studio-shell-integrated.md)。  
  
## <a name="isolated-mode"></a>隔离的模式  
 隔离的模式可让你可以创建自定义运行并排显示的工具与其他版本的 Visual Studio。 它主要适用于可以访问 Visual Studio 服务，无需根据所有标准的 Visual Studio 功能的工具。 你可以自定义基于 Visual Studio 独立 shell 应用程序的外观。 你可以轻松地关闭的功能和不希望与你的应用程序一起显示的菜单命令组。  
  
 有关详细信息，请参阅[Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>分发集成或独立 Shell 应用程序  
 若要发布集成或独立 shell 应用程序，你需要以包括你的应用程序、 可再发行组件，特殊集成或独立 shell 和安装程序。 有关分发和安装的详细信息，请参阅[分发独立 Shell 应用程序](../extensibility/distributing-isolated-shell-applications.md)。  
  
> [!IMPORTANT]
>  [最终用户许可协议 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) shell 的 Visual Studio 集成，并隔离包含一个有关数据收集节 (**第 3 部分。数据**)。  它描述从用户到你的应用程序生成的任一集成或独立 shell 软件可能由 Microsoft 收集的客户使用情况数据。 有关详细信息，请参阅[Microsoft Visual Studio 产品系列隐私声明](https://www.visualstudio.com/en-us/dn948229)。  
>   
>  如果从你的客户收集单独使用情况数据，通过应用程序，你必须向你收集的应用程序的用户提供相应的通知。  当你将独立或集成 shell 软件分发作为应用程序的一部分，根据 Visual Studio 软件开发工具包许可证，您必须包括以下项之一：  
>   
>  -   最终用户许可协议，作为应用程序许可协议的一部分  
> -   你自己需要你客户同意保护 Visual Studio 的条款的 EULA 集成或隔离 shell 至少多作为命令行程序软件的 Microsoft 最终用户许可条款  
  
## <a name="additional-resources"></a>其他资源  
 有关可再发行组件包的详细信息，请参阅[Visual Studio 扩展性下载](http://go.microsoft.com/fwlink/?LinkID=119298)Web 站点。  
  
## <a name="see-also"></a>另请参阅  
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)