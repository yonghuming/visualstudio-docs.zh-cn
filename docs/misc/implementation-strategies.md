---
title: "实现策略 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage，实现策略"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 实现策略
你可以使用自动化外接程序、VSPackage、Managed Extensibility Framework \(MEF\) 组件部分或三者的组合扩展 Visual Studio。 通常情况下，外接程序更易开发，但没有 VSPackage 或 MEF 组件部分强大。 外接程序可以调用扩展性接口，而 VSPackage 和 MEF 组件部分可以访问 Visual Studio 自动化模型。 你可以组合多个不同的方法来创建有效的解决方案。  
  
 可以在非托管或托管的代码中编写 VSPackage。 我们建议你使用托管包框架 \(MPF\) 在托管代码中编写新的 VSPackage。 几乎所有能写入非托管代码中的内容都可以更轻松、更安全地在托管代码中实现。 但是，非托管代码中编写的旧版应用程序将继续在 Visual Studio 中运行。  
  
 简单扩展可以向 Visual Studio UI 元素添加工具窗口或发送信息，如状态栏或输出窗口。 更复杂的应用程序也可被编写为 Visual Studio 层次结构，如服务器资源管理器。 通过实现项目、编辑器或设计器仍可以获取更多的能力。 例如，[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 本身作为语言服务实现。  
  
## 相关章节  
 [Visual Studio SDK 和自动化](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 讨论使用自动化、VSPackage 或两者的组合来创建 Visual Studio 扩展性应用程序。  
  
 [Visual Studio SDK 和托管代码](/visual-cpp/misc/visual-studio-sdk-and-managed-code)  
 比较在托管代码中编写 VSPackage 的不同方法。  
  
 [Visual Studio IDE 概念](/visual-cpp/misc/visual-studio-ide-concepts)  
 讨论 VSPackage 的基本信息以及如何使用服务。  
  
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 讨论 Visual Studio 中的常用 UI 应用程序元素，如状态和输出窗口。  
  
 [在 Visual Studio 中的层次结构](../extensibility/internals/hierarchies-in-visual-studio.md)  
 提供 Visual Studio 层次结构的概述，这将在集成开发环境 \(IDE\) 中显示为节点树。  
  
 [项目](../extensibility/internals/projects.md)  
 提供项目概述和解决方案类。  
  
 [编辑器和语言服务扩展](../extensibility/editor-and-language-service-extensions.md)  
 介绍如何扩展代码和文本编辑器以及如何创建自定义编辑器和设计器。  
  
 [遗留语言服务可扩展性](../extensibility/internals/legacy-language-service-extensibility.md)  
 演示如何创建语言服务。  
  
 [Visual Studio SDK 参考](../extensibility/visual-studio-sdk-reference.md)  
 VSSDK 的参考文档。  
  
## 请参阅  
 [开始开发 Visual Studio 扩展](../extensibility/starting-to-develop-visual-studio-extensions.md)