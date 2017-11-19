---
title: "Visual Studio Tools for Office Runtime 安装方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Visual Studio Tools for Office runtime, installation scenarios
ms.assetid: 71f34daf-8163-4a53-a401-9cab6581f30d
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e09d83fefee766ce19c71812bccfa751cc90e27e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools for Office Runtime Installation Scenarios
  可用三种方式安装 Visual Studio 2010 Tools for Office Runtime：  
  
-   安装 Visual Studio 时。  
  
-   安装 Microsoft Office 时。  
  
-   安装 Visual Studio 2010 Tools for Office Runtime 可再发行组件时。  
  
 安装的运行时组件取决于计算机的配置和安装方案。  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>每个安装方案中安装的运行时组件  
 Visual Studio 2010 Tools for Office Runtime 包括三个组件：Office 解决方案加载程序、.NET Framework 3.5 的 Office 扩展以及 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的 Office 扩展。 在安装运行时时，始终安装 Office 解决方案加载程序。 .NET Framework 的 Office 扩展的安装取决于计算机的配置和安装方案。 如果在首次安装运行时时 Office 扩展之一不能安装，则当满足某些需求时，运行时将稍后自动安装缺少的 Office 扩展。 运行时该功能被称为*按需安装*。  
  
 下表显示每个运行时安装方案中默认安装的运行时组件。 有关每个方案的详细信息将在后面显示。  
  
|运行时安装方案|Office 解决方案加载程序|.NET Framework 3.5 的 Office 扩展|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Office 扩展|[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 扩展|  
|-----------------------------------|----------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|通过 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 及更高版本|是|是的，如果已安装 .NET Framework 3.5。|是|是|  
|通过 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|是|是的，如果已安装 .NET Framework 3.5。|No|否|  
|通过 Office 2010 Service Pack 1 (SP1) 或更高版本|是|是的，如果已安装 .NET Framework 3.5。|是的，如果已安装 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。|否|  
|通过运行时可再发行组件|是|是的，如果已安装 .NET Framework 3.5|是的，如果已安装 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。|是的，如果已安装 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]。|  
  
### <a name="installing-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>使用 Visual Studio 或 Microsoft Office Developer Tools for Visual Studio 安装运行时  
 在 Visual Studio 中安装 Office 开发人员工具时，[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 和 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Office 扩展始终安装在开发计算机上。 仅当 .NET Framework 3.5 已位于开发计算机上时，才会安装 .NET Framework 3.5 的 Office 扩展。 如果在安装 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 后安装 .NET Framework 3.5，则在首次创建面向 .NET Framework 3.5 的 Office 项目时，运行时将自动安装 .NET Framework 3.5 的 Office 扩展。  
  
> [!WARNING]  
>  不能使用 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 或更高版本创建面向 .NET Framework 3.5 的 Office 项目。  
  
 有关如何安装 Office 开发人员工具的详细信息，请参阅[如何： 配置计算机以开发 Office 解决方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)。  
  
### <a name="installing-the-runtime-with-office"></a>使用 Office 安装运行时  
 安装 Office 时，如果 .NET Framework 3.5 已位于计算机上，则安装 .NET Framework 3.5 的 Office 扩展。 如果在安装 Office 之后安装 .NET Framework 3.5，则在 Office 应用程序首次尝试加载面向 .NET Framework 3.5 的解决方案时，运行时将自动安装 .NET Framework 3.5 的 Office 扩展。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的 Office 扩展不与 Office 一起安装，即使安装 Office 时 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本已存在。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Office 扩展随 Office 一起安装。 最终用户可以通过安装 Windows 更新来获得 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 扩展。  
  
 若要确保你的用户有必要的扩展以使用你的应用程序，将 Visual Studio 2010 Tools for Office Runtime 可再发行组件的最新版本作为你的解决方案的必备组件。 有关先决条件的详细信息，请参阅[用于部署的 Office 解决方案必备组件](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e)。  
  
### <a name="installing-the-runtime-by-using-the-runtime-redistributable"></a>通过使用运行时可再发行组件安装运行时  
 通过手动运行 Visual Studio 2010 Tools for Office Runtime 可再发行组件或在部署 Office 解决方案时将可再发行组件作为必备组件，可以安装运行时。  
  
 假如使用 Visual Studio 2010 Tools for Office Runtime 可再发行组件安装运行时，则如果 .NET Framework 的相应版本已存在于计算机上，将安装 .NET Framework 3.5 的 Office 扩展和 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的 Office 扩展。 如果在运行时已安装的情况下计算机缺少 .NET Framework 的这些版本之一，则此时将不安装缺少的 .NET framework 版本的 Office 扩展。 如果你于稍后安装 .NET Framework 所缺少的版本，则下一次解决方案需要已安装（如果运行时与使用 ClickOnce 部署的解决方案一起安装）或已加载（如果运行时与使用 Windows Installer 部署的解决方案一起安装）扩展时，运行时将自动安装相应的 Office 扩展。  
  
 关于在 ClickOnce 解决方案中包含系统必备组件的详细信息，请参阅[如何： 在最终用户计算机上以运行 Office 解决方案的安装的先决条件](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。 有关如何手动安装可再发行组件包中的运行时的详细信息，请参阅[如何： 安装 Visual Studio Tools for Office 运行时可再发行组件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office 运行时中的程序集](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  