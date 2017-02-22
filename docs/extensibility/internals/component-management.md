---
title: "组件管理 | Microsoft Docs"
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
  - "安装 [Visual Studio SDK] 组件"
  - "安装 [Visual Studio SDK]，文件管理"
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 组件管理
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

任务单元在 Windows Installer 的引用 Windows Installer 组件 \(有时称为 WICs 或元素\)。  GUID 标识每个 WIC，是安装的基本单位和引用计数设置的使用 Windows Installer。  
  
 尽管可以使用多种产品创建 VSPackage 安装程序，本讨论假定使用 Windows Installer \(.msi\) 文件。  当创建安装程序，您必须正确地管理文件部署时，以便正确引用计数始终发生。  因此，该产品的不同版本不会干扰使用或进行重大组合请安装和卸载方案。  
  
 在 Windows Installer，引用计数出现在组件级别。  您必须仔细组织资源 —文件，注册表项，等等 \)到元素。  具有组织的其他级别 \(如模块、可能在不同情况下帮助的功能和产品时\)。  有关更多信息，请参见 [Windows 安装程序基础知识](../../extensibility/internals/windows-installer-basics.md)。  
  
## 创作并行安装的一组指南  
  
-   创作在版本之间共享到元素的文件和注册表项。  
  
     这将在下一版本可以轻松地使用它们。  例如，键入全局注册的库，文件扩展名，在 HKEY\_CLASSES\_ROOT 注册的其他项目，依此类推。  
  
-   组共享组件到单独的合并模块中。  
  
     这有助于对并行至正确编写。  
  
-   通过在版本中，的相同 Windows Installer 组件安装共享文件和注册表项。  
  
     如果您使用不同的元素，文件和注册表项被卸载，在一、 VSPackage 卸载，但仍安装其他 VSPackage。  
  
-   不要组合在同一元素的版本和共享项目。  
  
     这使不能将共享的项添加到全局位置和已进行版本管理的项到独立位置。  
  
-   非共享指向受版本控制的文件的注册表项。  
  
     否则，共享密钥将被复盖，当安装了另一版本 VSPackage。  在移除后第二个版本，的文件键转到点。  
  
## 请参阅  
 [共享和版本控制的 Vspackage 之间进行选择](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage 安装方案](../../extensibility/internals/vspackage-setup-scenarios.md)