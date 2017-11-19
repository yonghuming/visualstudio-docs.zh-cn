---
title: "创建项目类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7c0bba9b80e4e874f222ce00834f44a2d93e3e7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-types"></a>创建项目类型
你可以扩展[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过创建新的项目类型。 若要创建新的项目类型，必须了解几个概念，并完成大量的步骤。 以下主题提供如何创建项目类型的概述。  
  
## <a name="in-this-section"></a>本节内容  
 [项目类型设计决策](../../extensibility/internals/project-type-design-decisions.md)  
 讨论项、 项目文件持久性，以及必须在创建新的项目类型之前做出的承诺机械师设计决策。  
  
 [清单：新建项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)  
 概述创建新的项目类型支持作为编辑代码和编译、 生成、 调试和部署你的项目中的应用程序的编程任务时必须遵循的步骤。  
  
 [使用项目工厂创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 提供有关如何提供和使用项目工厂来创建新项目的实例的信息。  
  
 [注册项目类型](../../extensibility/internals/registering-a-project-type.md)  
 提供语句从注册表提供的默认路径和数据和表包含从每个语句的注册表脚本的项的代码的示例。  
  
 [项目持久性](../../extensibility/internals/project-persistence.md)  
 讨论使用`IPersistFileFormat`以保留文件和非基于文件的项目对象。  
  
 [使用 MSBuild](../../extensibility/internals/using-msbuild.md)  
 介绍如何使用你的项目类型[!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)]生成引擎以使用户可以从生成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]然后在命令行中。  
  
## <a name="related-sections"></a>相关章节  
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 说明如查看工具的代码的体系结构**对象浏览器**和**类视图**窗口。 描述的接口和用于在 VSPackage 中实现浏览对象的方法。  
  
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 讨论项目播放在确定哪种编辑器使用打开的项目项时的重要性和可以对操作项目资源的方法。  
  
 [使用 Windows Installer 安装 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 演示如何为你的 VSPackage 提供其自己的唯一标识以及如何将你的 VSPackage Dll 和其他信息包装在 Windows Installer 包 (。MSI 文件） 以部署到你的客户。  
  
 [Visual Studio 中的层次结构](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 描述如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]视图和地址的层次结构。  
  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 提供的 VSPackage，扩展的可安装的 COM 对象概述[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境，并讨论了如何实现你自己的 VSPackage。  
  
 [项目类型](../../extensibility/internals/project-types.md)  
 讨论如何使用项目来修改代码、 编译和生成代码，并运行和调试代码，并提供指向有关如何创建项目类型的详细主题。