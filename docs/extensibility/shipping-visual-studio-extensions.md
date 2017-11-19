---
title: "传送 Visual Studio 扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf74110cf42daa51521cc7ea706c1b951b23deb8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="shipping-visual-studio-extensions"></a>传送 Visual Studio 扩展
完成开发你的扩展后，你可以安装在其他计算机上、 与你的好友和同事共享它或将其发布在 Visual Studio Marketplace 上。 在本部分中，我们介绍你需要执行为了发布和维护你的扩展的所有操作： 使用.vsix 文件，发布、 本地化，和更新。  
  
## <a name="working-with-vsix-extensions"></a>使用 VSIX 扩展  
 你可以创建 VSIX 扩展，通过创建一个空白的 VSIX 项目中，然后将不同的项模板添加到它。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
 你可以使用 VSIX 格式打包项目模板、 项模板，Vspackage，Managed Extensibility Framework (MEF) 组件，**工具箱**控件、 组件和自定义类型 （这包括自定义起始页）。 VSIX 格式使用基于文件的部署。 有关 VSIX 包的详细信息，请参阅[剖析 VSIX 包](../extensibility/anatomy-of-a-vsix-package.md)。  
  
 VSIX 格式不支持代码段的安装。 它也不支持某些其他方案，如写入到全局程序集缓存 (GAC) 或对系统注册表。 如果你需要向 gac 中或在安装中的注册表写入，则必须使用 Windows Installer。 有关详细信息，请参阅[准备扩展为 Windows Installer 部署](../extensibility/preparing-extensions-for-windows-installer-deployment.md)。  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>到 Visual Studio 应用商店中发布你的扩展  
 你可以只需通过邮寄它们.vsix 文件，或在服务器上将放在分发给其他人扩展。 但在很多人手中获取你的代码的最佳方法是将其放入[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 可以使用 Visual Studio 用户可通过 visual Studio Marketplace 扩展**扩展和更新**。 有关详细信息，请参阅[查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)。  
  
 有关演示如何将扩展上载到 Visual Studio 应用商店的完整示例，请参阅[演练： 发布 Visual Studio 扩展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。  
  
## <a name="private-galleries"></a>Private Galleries  
 当你开发控件、 模板和工具，你可以将它们发布到你的 intranet 上私有库与你的组织共享它们。 有关详细信息，请参阅[私有库](../extensibility/private-galleries.md)。  
  
## <a name="localizing-your-extension"></a>本地化你的扩展  
 如果你计划要释放你在不同的区域设置中的扩展，则应考虑对它进行本地化。 有关所涉及的内容的说明，请参阅[本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="updating-and-versioning-your-extension"></a>更新和版本管理你的扩展  
 已发布你的扩展后，将出现一次当你需要更新它。 若要了解如何更新已在 Visual Studio Marketplace 发布的扩展，请参阅[如何： 更新扩展](../extensibility/how-to-update-a-visual-studio-extension.md)。  
  
 你可以设置你的扩展以支持多个版本的 Visual Studio。 有关详细信息，请参阅[支持多个 Visual Studio 版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[VSIX 项目模板入门](../extensibility/getting-started-with-the-vsix-project-template.md)|说明如何使用 VSIX 项目模板来安装自定义项目模板。|  
|[VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)|描述 VSIX 包的组件。|  
|[VSIX 项目模板](../extensibility/vsix-project-template.md)|提供有关如何打包和发布扩展的分步说明。|  
|[本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)|说明如何通过使用 extension.vsixlangpack 文件为安装过程中提供本地化的文本。|  
|[如何： 更新扩展](../extensibility/how-to-update-a-visual-studio-extension.md)|描述如何更新你的系统上的某个扩展以及如何将更新部署到现有的 Visual Studio 扩展。|  
|[如何：将依赖项添加到 VSIX 包](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|介绍如何将引用添加到 VSIX 部署包。|  
|[准备 Windows Installer 部署的扩展](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|说明如何将使用 Windows Installer 你扩展部署。|  
|[对 VSIX 包进行签名](../extensibility/signing-vsix-packages.md)|说明如何 VSIX 包进行签名。|  
|[专用库](../extensibility/private-galleries.md)|说明如何创建专用库的扩展。|  
|[支持多个版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|演示如何扩展支持多个版本的 Visual Studio。|
|[查找 Visual Studio](locating-visual-studio.md)|描述如何找到 Visual Studio 的自定义扩展部署的实例。|
