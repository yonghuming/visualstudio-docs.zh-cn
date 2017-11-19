---
title: "导致自动化模型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5907f540e5f81e26b7d184352e3c38531ec5da66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="contributing-to-the-automation-model"></a>Contributing to the Automation Model
Visual Studio 为自定义环境提供一组自动化接口。 自动化模型是使最终用户能够创建 Visual Studio 外接程序和扩展的对象模型。  
  
 此外，它适合于你，作为 VSPackage 开发人员，以参与自动化模型;通过执行此操作，使你的 VSPackage 创建外接程序和在使用你的 VSPackage 中时，通常情况下提供一致的用户模型体验的最终用户[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 为了使最终用户体验一致，你可以遵循一组的准则，以便你的 VSPackage 的自动化模型遵循中的想法设计你的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="in-this-section"></a>本节内容  
 [自动化模型概述](../../extensibility/internals/automation-model-overview.md)  
 定义自动化模型控制常见环境的主要方面的对象相关的组。 此组的对象图中的自动化模型关系图。  
  
 [提供适用于 VSPackage 的自动化](../../extensibility/internals/providing-automation-for-vspackages.md)  
 讨论提供自动化你的 VSPackage 的两种主要方法。  
  
 [公开项目对象](../../extensibility/internals/exposing-project-objects.md)  
 提供用于创建 VSPackage 特定对象的分步说明。  
  
 [项目建模](../../extensibility/internals/project-modeling.md)  
 说明创建新的项目类型的自动化所需的标准项目对象，并阐明项目自动化遵循的路径。 本主题还提供的声明和实现类的列表。  
  
 [公开事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 提供有关创建事件为您的自动化模型的分步说明。  
  
 [选项页的自动化支持](../../extensibility/internals/automation-support-for-options-pages.md)  
 介绍如何为支持的 VSPackage 的属性的自定义返回自动化对象**选项**对话框中，在**工具**通过扩展菜单`DTE.Properties`对象。  
  
 [提供适用于 Code 的自动化](../../extensibility/internals/providing-automation-for-code.md)  
 说明创建自动化模型为你的代码不需要。 但是，提供到代码模型真知灼见信息本主题中提供的链接。  
  
 [如何：提供适用于 Windows 的自动化](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 说明，每当你想要使自动化对象在一个窗口，并且环境不提供现成的自动化对象，提供自动化是一个好主意。 讨论的工具窗口与文档窗口的自动化。  
  
 [使用自动化模型](../../extensibility/internals/using-the-automation-model.md)  
 提供演示如何自动化使用者获取初始项目自动化对象的两个代码示例。  
  
 [Configuration 和 SelectedItem 对象的自动化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 提供有关配置选项的自动化和自动化将所选项目的信息。  
  
## <a name="reference"></a>参考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 提供演示如何 VSPackage 参与 DTE 自动化对象模型的代码示例。 列出参数、 返回值和所选的备注。  
  
## <a name="related-sections"></a>相关章节