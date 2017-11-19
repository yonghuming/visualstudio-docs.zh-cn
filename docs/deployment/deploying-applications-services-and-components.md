---
title: "部署应用程序、 服务和组件 |Microsoft 文档"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 9d9aeaa80aa054b8178adbfc707b1537449776d7
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="deploying-applications-services-and-components"></a>部署应用程序、服务和组件

通过部署应用程序、服务或组件，你可以将其分发以便安装于其他计算机、设备、服务器或云中。 你需要在 Visual Studio 中为所需的部署类型选择适当的方法。  
  
下表介绍了不同的部署方案，并提供指向每个方案的详细信息。  

创建 Windows 应用程序的安装程序体验的选项的讨论，请参阅[桌面到通用 Windows 平台 (UWP) 桥](/windows/uwp/porting/desktop-to-uwp-root#convert)。

 
## <a name="in-this-section"></a>本节内容  
  
| 部署方案 | 支持内容 |
| --- | --- |  
| **发布到云：**你可以提供应用程序、 服务和数据从任意位置通过使用 Visual Studio 将它们部署到 Microsoft Azure。|[应用程序发布到 Microsoft Azure](http://msdn.microsoft.com/library/windowsazure/ee460772.aspx) |
| **发布 Windows 应用程序：**可以轻松地生成、 提交，和销售给世界各地的客户从 Microsoft 应用商店应用。 |[发布 Windows 应用](https://developer.microsoft.com/store/publish-apps) |
| **部署 ASP.NET 应用程序或服务：**可采用多种不同方式部署 ASP.NET 应用程序和服务。|[部署 ASP.NET web 应用程序和服务](http://www.asp.net/aspnet/overview/deployment) |
| **发布 Office 外接程序：**可以在从 Visual Studio 的 Office 外接程序中发布。 | [部署和发布 Office 外接程序](https://dev.office.com/docs/add-ins/publish/publish) |
| **部署 WCF 或 OData 服务：**其他应用程序可以使用你部署到 web 服务器的 WCF RIA 服务。 | [开发和部署 WCF 数据服务](https://docs.microsoft.com/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **部署桌面应用程序：**通过使用 ClickOnce 部署，你可以将发布到 web 服务器或网络文件共享的桌面应用程序。 用户随后只需一次单击即可安装应用程序。 | [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md) |
| **部署 Visual c + + 应用程序：**可以通过使用集中部署、 本地部署或静态链接部署 Visual c + + 运行时与应用程序。 | [部署本机桌面应用程序 (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp.md) |
| **创建安装程序：**基于 MSI 的 WiX 安装程序可以使用创建[WiX 工具集 Visual Studio 2017 扩展](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。 请注意，InstallShield Limited Edition 已不再包含在 Visual Studio;咨询[Flexera 软件](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)有关 Visual Studio 2017 的可用性。 |
| **部署用于测试的应用程序：**可以启用更复杂的开发和测试部署到虚拟环境的应用程序。|[测试实验室环境](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md) | 
| **安装必备组件：**你可以通过配置一般安装程序，这被称为引导程序安装桌面应用程序的系统必备组件。|[应用程序部署必备](../deployment/application-deployment-prerequisites.md) |
| **部署 LightSwitch 应用程序或服务：** LightSwitch 中 Visual Studio 2017，不再受支持，但仍可以从 Visual Studio 2015 及更早版本部署。 | [部署 LightSwitch 应用程序](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |  
