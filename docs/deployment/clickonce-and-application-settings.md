---
title: "ClickOnce 和应用程序设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fbe35de06ac09c95a045748a5d8ecb379779a20a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 和应用程序设置
Windows 窗体的应用程序设置，可以轻松创建、 存储和维护自定义应用程序和客户端上的用户首选项。 以下文档介绍了在 ClickOnce 应用程序中，应用程序设置文件的工作原理以及用户升级到下一个版本时，ClickOnce 如何迁移设置。  
  
 下面的信息仅适用于默认应用程序设置提供程序，<xref:System.Configuration.LocalFileSettingsProvider>类。 如果提供自定义提供程序，它将其数据的存储和如何升级版本之间其设置将确定该提供程序。 应用程序设置提供程序的详细信息，请参阅[应用程序设置体系结构](/dotnet/framework/winforms/advanced/application-settings-architecture)。  
  
## <a name="application-settings-files"></a>应用程序设置文件  
 应用程序设置使用两个文件：*应用*。.exe.config 并且 user.config，其中*应用*是 Windows 窗体应用程序的名称。 user.config 创建应用程序存储用户范围的设置的客户端第一个时间。 *应用*。 exe.config，与此相反，如果会存在在部署之前定义设置的默认值。 Visual Studio 将自动地包括此文件，当你使用其**发布**命令。 如果创建 ClickOnce 应用程序使用 Mage.exe 或 MageUI.exe 中，你必须确保此文件是包含你的应用程序的其他文件时填充你的应用程序清单。  
  
 在 Windows 窗体应用程序中不使用 ClickOnce，应用程序部署*应用*。.exe.config 文件存储在应用程序目录中，而 user.config 文件存储在用户的**Documents and Settings**文件夹。 在 ClickOnce 应用程序，*应用*。 exe.config 驻留在 ClickOnce 应用程序缓存中，内部的应用程序目录和 user.config 驻留在该应用程序的 ClickOnce 数据目录。  
  
 无论你部署你的应用程序的方式，应用程序设置确保安全的读取访问权限*应用*。.exe.config，并且对 user.config 安全的读/写访问。  
  
 在 ClickOnce 应用程序中，使用应用程序设置的配置文件的大小受 ClickOnce 缓存的大小的约束。 有关详细信息，请参阅[ClickOnce 缓存概述](../deployment/clickonce-cache-overview.md)。  
  
## <a name="version-upgrades"></a>版本升级  
 正如每个版本的 ClickOnce 应用程序是独立于所有其他版本，则 ClickOnce 应用程序的应用程序设置是独立的以及其他版本的设置。 在你的用户升级到更高版本的应用程序，应用程序设置会将针对提供的更新的版本和合并到一组新的设置文件的设置的设置设置的最新 （最高编号） 版本设置进行比较。  
  
 下表描述了应用程序设置如何判断要复制的设置。  
  
|更改类型|升级操作|  
|--------------------|--------------------|  
|设置已添加到*应用*。 exe.config|新的设置合并到当前版本的*应用*。 exe.config|  
|删除从设置*应用*。 exe.config|从当前版本中删除旧的设置*应用*。 exe.config|  
|设置的默认值已更改;本地设置仍然设置为原始默认值在 user.config|设置作为值合并到新的默认值与当前版本的 user.config|  
|设置的默认值已更改;设置设置为非默认值在 user.config|设置与保留的非默认值合并到当前版本的 user.config|  
  
 如果你已创建你自己的应用程序设置包装类，并且想要自定义更新逻辑，则可以重写<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A>方法。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce 和漫游设置  
 ClickOnce 并不适用于漫游设置，它允许你设置文件，以便在网络上计算机之间跟随您。 如果你需要漫游设置，你将需要为实现将设置存储在网络上的应用程序设置提供程序或开发您自己的自定义设置类来存储远程计算机上的设置。 设置提供程序中的详细信息，请参阅[应用程序设置体系结构](/dotnet/framework/winforms/advanced/application-settings-architecture)。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [应用程序设置概述](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [ClickOnce 缓存概述](../deployment/clickonce-cache-overview.md)   
 [在 ClickOnce 应用程序中访问本地数据和远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)