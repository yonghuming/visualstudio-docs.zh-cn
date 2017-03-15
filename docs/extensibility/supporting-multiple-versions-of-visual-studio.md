---
title: "支持多个版本的 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 中，支持多个版本"
  - "Vspackage，通过并行兼容性"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 支持多个版本的 Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

术语 *通过并行* 意味着您可以安装和维护多个版本的同一台计算机上的产品。 对于 Vspackage，这意味着用户可以具有多个 Visual Studio 版本安装在同一台计算机上。 但是，不能有您 VSPackages 迁移加载到 Visual Studio 的一个版本的并行的版本。  
  
 使你能够被加载到 Visual Studio 的版本的并行的 VSPackage 之前，请考虑以下方面:  
  
-   您必须确定您想要跟踪哪些通过并行实施策略。  
  
     有关详细信息，请参阅[共享和版本控制的 Vspackage 之间进行选择](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。  
  
-   您的解决方案和项目文件的格式必须能够容纳实施策略。  
  
     有关详细信息，请参阅 [升级自定义项目](../misc/upgrading-custom-projects.md) 和 [注册由并行部署的文件扩展名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   安装程序必须处理实施策略，以便进行版本控制的组件，以及在所有版本间共享的组件已正确安装并注册。  
  
     有关详细信息，请参阅 [使用 Windows Installer 安装 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md) 以及 [组件管理](../extensibility/internals/component-management.md)。  
  
    > [!NOTE]
    >  安装 Visual Studio 的版本也将安装相应版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 例如，在同一台计算机上安装 Visual Studio 2010 和 Visual Studio 2012 还将安装的版本 4.0 和 4.5 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], 分别。  
  
## 本节内容  
 [共享和版本控制的 Vspackage 之间进行选择](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 说明如何解决你的 VSPackage 中的并行的问题。  
  
 [注册由并行部署的文件扩展名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 描述你的 VSPackage 如何通过并行方案中注册文件关联。  
  
## 相关章节  
 [安装 VSPackage](../misc/installing-vspackages.md)  
 讨论如何构建和安装 Vspackage 以及如何支持同时运行多个版本的 Visual Studio 的用户。