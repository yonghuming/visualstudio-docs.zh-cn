---
title: "源控件插件体系结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件，体系结构"
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 源控件插件体系结构
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

可以添加数据源控件支持对 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成开发 \(IDE\)环境通过实现和附加源代码管理插件。  IDE 连接到源代码管理插件定义完善的源代码管理插件 API。  IDE 通过提供包括工具栏和菜单命令的用户界面公开 \(UI\)源代码管理系统的版本控制功能。  源代码管理插件实现源代码管理功能。  
  
## 源代码管理插件资源  
 源代码管理插件提供资源可帮助创建和连接版本的应用程序。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  源代码管理插件包含必须由源代码管理插件实现的 API 规范，以便可以集成到 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  它还包含一个代码示例 \(编写在 C\+\+\) 实现重要功能的一个主干源代码管理插件演示的实现符合源代码管理插件 API。  
  
 ，如果您在所需创建源代码管理 DLL 设置功能实现使用源代码管理插件 API 匹配，源代码管理插件 API 规范充分利用选择的所有源代码管理系统。  
  
## 组件  
 在关系图的源控件适配器包是将用户请求源代码管理操作转换为函数调用支持受源代码管理插件 IDE 的元素。  为了使发生，将此 IDE 和源代码管理插件必须具有来回传递信息 IDE 中该插件之间的有效对话框。  为了使出现此的对话框，它们必须都使用同一种语言。  本文档概述的源代码管理插件 API 是此替换的常见术语。  
  
 ![源代码管理体系结构示意图](~/extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs\_sccsdk\_plug\_in\_arch")  
显示交互之间的和源代码管理插件的体系结构关系图  
  
 根据体系结构示意图所示， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell，标记对关系图的 shell，以承载用户的工作计划和关联的元素，如编辑和解决方案资源管理器。  源控件适配器包处理 IDE 和源代码管理插件之间的交互。  源控件适配器包提供自己的数据源控件 UI。  它是顶级 UI 用户交互以启动和定义源代码管理操作的大小。  
  
 源代码管理插件可以有它的 UI，如该图所示，可以包括两部分。  标记为 “供应商的框 UI”表示您，作为源代码管理插件创建者，提供的自定义用户界面元素。  ，当用户调用高级源代码管理操作时，这些直接由源代码管理插件显示。  标记为 “帮助器的框 UI”是通过设置 IDE 间接调用的源代码管理插件 UI 功能。  源代码管理插件通过与用户界面相关的消息到 IDE 通过提供的特殊回调函数 IDE。  帮助器 UI 便于与 IDE 的一个无缝集成 \(通常使用 **高级** 按钮\) 从而提供一种统一的最终用户体验。  
  
 源代码管理插件无法进行更改 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell，因此，因此，对 IDE 或源代码控制 UI 提供的源控件适配器包。  它必须进行通过使最终用户的集成体验各种数据源控件插件 API 函数的实现提供的最大使用此灵活性。  源代码管理插件 API 文档的引用部分包括一些高级源代码管理插件功能的信息。  若要利用这些功能，源代码管理插件必须声明它的高级功能到 IDE 在初始化时，因此，它必须实现每个函数的给定最新机能。  
  
## 请参阅  
 [源代码管理插件](../../extensibility/source-control-plug-ins.md)   
 [词汇表](../../extensibility/source-control-plug-in-glossary.md)   
 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)