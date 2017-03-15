---
title: "Shell （独立或集成） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ed0e82dbc2c093a94080fe3fcf07a3e3b20e1a50
ms.lasthandoff: 02/22/2017

---
# <a name="shell-isolated-or-integrated"></a>Shell （独立或集成）
在集成在一起或独立模式下，您可以创建自己的基于 Visual Studio 的应用程序。 在集成模式下，除了你的应用程序提供了很多 Visual Studio 功能。 在独立模式下，您可以选择您希望与您自己的扩展插件一起分发的 Visual Studio 功能的子集。  
  
## <a name="integrated-mode"></a>集成模式下  
 集成模式下使用户能够使用标准的 Visual Studio 功能以及自定义工具。 该集成的 shell 主要供托管编程语言和软件开发工具。  
  
 自动生成在集成外壳程序的自定义工具将与其他任何版本的 Visual Studio 安装在同一台计算机上的合并。 如果尚未安装 Visual Studio，可以提供集成的 Visual Studio shell 的可再发行组件版本。  
  
 Visual Studio 集成 shell 的可再发行组件版本不包括编程语言和支持其相应项目系统的功能。  
  
> [!NOTE]
>  Visual Studio shell 集成模式下可以与所有版本的 Visual Studio 速成版除外一起安装。  
  
 有关详细信息，请参阅[Visual Studio Shell （集成）](../extensibility/visual-studio-shell-integrated.md)。  
  
## <a name="isolated-mode"></a>隔离的模式  
 独立的模式允许您创建通过并行运行的自定义工具与其他版本的 Visual Studio。 它是主要适用于可以访问 Visual Studio 服务而无需根据所有标准的 Visual Studio 功能的工具。 您可以自定义上隔离的 Visual Studio shell 构建应用程序的外观。 您可以轻松地关闭功能并不希望与您的应用程序一起显示的菜单命令组。  
  
 有关详细信息，请参阅[Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>将应用程序集成在一起或独立的命令行程序分发  
 若要发布应用程序集成在一起或独立的命令行程序，您需要包括您的应用程序、 可再发行组件，一个特殊集成在一起或独立外壳和安装程序。 有关分发和安装的详细信息，请参阅[分发独立外壳应用程序](../extensibility/distributing-isolated-shell-applications.md)。  
  
> [!IMPORTANT]
>  [最终用户许可协议 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552)外壳程序的 Visual Studio 集成，并隔离包括一节介绍了数据收集 (**第 3 部分。Data**).  它描述从任一融入您的应用程序的集成在一起或独立的命令行程序软件的用户可能由 Microsoft 收集的客户使用情况数据。 有关详细信息，请参阅[Microsoft Visual Studio 产品系列隐私声明](https://www.visualstudio.com/en-us/dn948229)。  
>   
>  如果从客户收集单独使用情况数据，通过应用程序，您必须向您收集的应用程序的用户提供适当的通知。  独立或集成 shell 软件分发作为应用程序中，根据 Visual Studio 软件开发工具包许可证的一部分时必须包括以下项之一︰  
>   
>  -   最终用户许可协议为应用程序许可证的一部分  
> -   需要您的客户同意保护 Visual Studio 的条款自己 EULA 集成或外壳程序有时更具隔离作为 shell 软件 Microsoft 最终用户许可条款  
  
## <a name="additional-resources"></a>其他资源  
 有关可再发行组件包的详细信息，请参阅[Visual Studio 扩展性下载](http://go.microsoft.com/fwlink/?LinkID=119298)Web 站点。  
  
## <a name="see-also"></a>另请参阅  
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)
