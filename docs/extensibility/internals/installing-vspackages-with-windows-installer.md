---
title: "使用 Windows Installer 安装 Vspackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "使用 Windows Installer 的安装 [Visual Studio SDK]"
  - "Vspackage 部署"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用 Windows Installer 安装 Vspackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

集成 VSPackage 到 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中需要更多的文件复制到用户的计算机。  VSPackage 的安装程序必须安装 VSPackage 及其依赖文件和注册并将它们 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  VSPackage 可以利用集成功能 \(如显示一个图标在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 初始屏幕和有关对话框。  
  
 Microsoft Windows Installer 文件是推荐的使用方式分配 Vspackage。  易于使用 Windows Installer 包在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支持的所有 windows 操作系统中运行。  有关更多信息，请参见 [Windows Installer](http://msdn.microsoft.com/zh-cn/121be21b-b916-43e2-8f10-8b080516d2a0)。  
  
## 本节内容  
 [Windows 安装程序基础知识](../../extensibility/internals/windows-installer-basics.md)  
 提供 Windows Installer 的概述。  
  
 [VSPackage 安装方案](../../extensibility/internals/vspackage-setup-scenarios.md)  
 讨论可以支持 Vspackage 和 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的并行安装的不同方法。  
  
 [创作 Windows Installer 包](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 提供安装程序遵循正确地安装和集成 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的典型的步骤概述。  
  
 [检测系统要求](../../extensibility/internals/detecting-system-requirements.md)  
 描述安装程序如何检测 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 及其元素和移除设置，如果 VSPackage 要求不匹配。  
  
 [组件管理](../../extensibility/internals/component-management.md)  
 讨论如何开发将维护前面的产品版本完整性的安装程序。  
  
 [为 VSPackage 选择的安装目录](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 摘要找到 Vspackage 的选项。  
  
 [VSPackage 注册](../../extensibility/internals/vspackage-registration.md)  
 讨论 Vspackage 如何注册在安装时，还可以自注册原因是一个不应。  
  
 [部署项目类型](../../extensibility/internals/deploying-project-types.md)  
 讨论如何为托管代码项目类型使用新项目类型的聚合函数。  
  
 [如何: 生成安装程序的注册表信息](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 解释如何使用 RegPkg.exe 生成注册清单用于管理的 VSPackage。  
  
 [必须在安装后运行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 解释如何运行安装后命令集成 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [卸载使用 Windows Installer VSPackage](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 描述该安装程序必须执行的步骤，当用户卸载 VSPackage 时。  
  
## 相关章节  
 [安装 VSPackage](../../misc/installing-vspackages.md)  
 讨论如何生成和安装 Vspackage 以及如何支持并发运行 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的多个版本的用户。