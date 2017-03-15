---
title: "创建项目类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新的项目类型"
  - "项目 [Visual Studio SDK]，新项目类型"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 创建项目类型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以扩展 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 通过创建新的项目类型。 若要创建新的项目类型，必须了解几个概念，并完成几个步骤。 以下主题提供有关如何创建项目类型的概述。  
  
## 本节内容  
 [项目类型的设计决策](../../extensibility/internals/project-type-design-decisions.md)  
 讨论项目、 项目文件持久性，以及必须在创建新的项目类型之前做出的承诺的机修工设计决策。  
  
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)  
 概述创建支持编辑代码和编译、 构建、 调试和部署项目中的应用程序的编程任务的新项目类型时必须遵循的步骤。  
  
 [通过使用项目工厂来创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 提供有关如何提供和使用项目工厂来创建新项目的实例的信息。  
  
 [注册一种项目类型](../../extensibility/internals/registering-a-project-type.md)  
 提供代码示例包含的语句的注册表中提供的默认路径和数据，以及一个表的每个语句的注册表脚本中的项。  
  
 [项目持久性](../../extensibility/internals/project-persistence.md)  
 介绍如何使用 `IPersistFileFormat` 以保留文件和非基于文件的项目对象。  
  
 [使用 MSBuild](../../extensibility/internals/using-msbuild.md)  
 介绍如何使用您的项目类型 [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] 构建引擎以使用户可以从生成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 和在命令行。  
  
## 相关章节  
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 介绍代码如查看工具的体系结构 **对象浏览器** 和 **类视图** 窗口。 描述的接口和方法，用于在 VSPackage 中实现对象浏览方式。  
  
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 讨论了在确定打开的项目项时，将使用的编辑器中播放的项目的重要性和可以对操作项目资源的方法。  
  
 [使用 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 演示如何为你的 VSPackage 提供其自己唯一的标识以及如何在 Windows 安装程序包包装 VSPackage Dll 和其他信息 \(。MSI 文件） 以部署到您的客户。  
  
 [在 Visual Studio 中的层次结构](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 描述如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 视图和地址的层次结构。  
  
 [Vspackage](../../extensibility/internals/vspackages.md)  
 提供的 VSPackage，扩展了非可安装的 COM 对象概述 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 环境，并讨论了如何实现你自己的 VSPackage。  
  
 [项目类型](../../extensibility/internals/project-types.md)  
 讨论如何使用项目来修改代码、 编译和生成的代码，以及运行和调试代码，并提供指向有关如何创建项目类型的详细主题的链接。