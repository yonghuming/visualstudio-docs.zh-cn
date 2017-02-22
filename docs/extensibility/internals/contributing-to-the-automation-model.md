---
title: "导致自动化模型 | Microsoft Docs"
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
  - "自动化 [Visual Studio SDK]"
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 导致自动化模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 提供一组自动化接口的自定义环境。 自动化模型是使最终用户能够创建 Visual Studio 加载项和扩展的对象模型。  
  
 此外，很适合于您，作为 VSPackage 开发人员，参与到自动化模型中;通过执行此操作，使你的 VSPackage 创建加载项并在使用你的 VSPackage 中时，通常情况下提供一致的用户模型体验的最终用户 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 若要使最终用户体验保持一致，可执行一组准则，以便你的 VSPackage 的自动化模型遵循中的观点设计你的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 本节内容  
 [自动化模型概述](../../extensibility/internals/automation-model-overview.md)  
 将自动化模型定义为相关的一组对象用于控制常见环境的主要方面。 此组对象图中的自动化模型关系图。  
  
 [提供有关 Vspackage 的自动化](../../extensibility/internals/providing-automation-for-vspackages.md)  
 讨论提供你的 VSPackage 的自动化的两种主要方法。  
  
 [公开项目对象](../../extensibility/internals/exposing-project-objects.md)  
 提供用于创建 VSPackage 特定对象的分步说明。  
  
 [项目建模](../../extensibility/internals/project-modeling.md)  
 解释创建新的项目类型的自动化所需的标准项目对象，并说明了项目自动化遵循的路径。 本主题还提供的声明和实现类的列表。  
  
 [公开事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 提供用于创建事件的自动化模型的分步说明。  
  
 [选项页的自动化支持](../../extensibility/internals/automation-support-for-options-pages.md)  
 描述如何将支持作为 VSPackage 的属性的自定义自动化对象 **选项** 对话框在 **工具** 菜单上，通过扩展 `DTE.Properties` 对象。  
  
 [提供代码的自动化](../../extensibility/internals/providing-automation-for-code.md)  
 介绍了创建自动化模型为您的代码不需要。 但是，在此主题，它提供到代码模型的深度信息中提供的链接。  
  
 [如何: 提供适用于 Windows 的自动化](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 解释，每当你想要使自动化对象在一个窗口，并且环境不提供现成的自动化对象，提供自动化是一个好主意。 讨论了自动化工具窗口和文档窗口。  
  
 [使用自动化模型](../../extensibility/internals/using-the-automation-model.md)  
 提供了两个代码示例演示如何自动化使用者获取初始项目自动化对象。  
  
 [有关配置和 SelectedItem 对象的自动化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 提供有关配置选项的自动化和自动化的所选项目添加信息。  
  
## 参考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 提供的代码示例，演示如何在 DTE 自动化对象模型中加入 VSPackage。 列出参数、 返回值，以及所选的备注。  
  
## 相关章节