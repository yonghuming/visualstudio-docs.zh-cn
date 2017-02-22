---
title: "传送 Visual Studio 扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 部署"
  - "部署中 VSIX"
  - "VSIX 包中的附属 Dll，"
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 传送 Visual Studio 扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

完成开发您的扩展后，可以在其他计算机上安装、 共享与朋友和同事，或将其发布在 Visual Studio 库上。 在本部分中，我们介绍您需要做以便在发布和维护您的扩展的所有操作: 使用.vsix 文件，发布、 本地化，以及更新。  
  
## 使用 VSIX 扩展  
 您可以通过创建一个空白的 VSIX 项目，然后将不同的项模板添加到它创建 VSIX 扩展。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
 您可以使用 VSIX 格式打包项目模板、 项模板，Vspackage，Managed Extensibility Framework \(MEF\) 组件 **工具箱** 控件、 组件和自定义类型 \(这包括自定义起始页\)。 VSIX 格式使用基于文件的部署。 VSIX 包的详细信息，请参阅 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)。  
  
 VSIX 格式不支持代码段的安装。 它也不支持某些其他方案，如写入到全局程序集缓存 \(GAC\) 或对系统注册表。 如果您需要向 gac 中或在安装中的注册表写入，则必须使用 Windows Installer。 有关详细信息，请参阅[为 Windows Installer 部署做好准备扩展](../extensibility/preparing-extensions-for-windows-installer-deployment.md)。  
  
## 到 Visual Studio 库发布您的扩展  
 您可以只需通过邮寄它们.vsix 文件或在服务器上将放在分发给其他人您的扩展。 但若要获取您的代码中的很多人的手中的最佳方式是将其放入 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)。 可以使用 Visual Studio 用户可以通过 visual Studio 库扩展 **扩展和更新**。 有关更多信息，请参见[查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)。  
  
 有关演示如何上载到 Visual Studio 库的扩展的完整示例，请参阅 [演练: 发布 Visual Studio 扩展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。  
  
## 私有库  
 在开发控件、 模板和工具时，您可以将它们发布到 intranet 上的专用库与您的组织共享它们。 有关更多信息，请参见[私有库](../extensibility/private-galleries.md)。  
  
## 本地化您的扩展  
 如果您打算发布您的扩展在不同的区域设置，则应考虑对它进行本地化。 有关所涉及的内容的说明，请参阅 [本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)。  
  
## 更新和版本控制您的扩展  
 已发布您的扩展后，将出现您需要更新它的时候。 若要了解如何更新已发布在 Visual Studio 库的扩展，请参阅 [如何︰ 更新扩展](../extensibility/how-to-update-a-visual-studio-extension.md)。  
  
 您可以设置您的扩展以支持多个版本的 Visual Studio。 有关更多信息，请参见[支持多个版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[Getting Started with VSIX 项目模板](../extensibility/getting-started-with-the-vsix-project-template.md)|说明如何使用 VSIX 项目模板来安装自定义项目模板。|  
|[VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)|描述一个 VSIX 包的组件。|  
|[VSIX 项目模板](../extensibility/vsix-project-template.md)|提供有关如何打包和发布扩展的分步说明。|  
|[本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)|说明如何通过使用 extension.vsixlangpack 文件为在安装过程中提供本地化的文本。|  
|[如何︰ 更新扩展](../extensibility/how-to-update-a-visual-studio-extension.md)|描述如何更新您的系统上的某个扩展以及如何将更新部署到现有的 Visual Studio 扩展。|  
|[如何︰ 添加对 VSIX 包的依赖项](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|描述如何将引用添加到 VSIX 部署包。|  
|[为 Windows Installer 部署做好准备扩展](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|说明如何部署与 Windows 安装程序扩展插件。|  
|[对 VSIX 包签名](../extensibility/signing-vsix-packages.md)|说明如何签署 VSIX 包。|  
|[私有库](../extensibility/private-galleries.md)|说明如何创建私有库也将为扩展。|  
|[支持多个版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|演示如何扩展插件支持多个版本的 Visual Studio。|