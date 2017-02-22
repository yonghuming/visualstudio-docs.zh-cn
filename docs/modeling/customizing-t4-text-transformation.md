---
title: "自定义 T4 文本转换 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, API"
  - "文本模板, 自定义宿主"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
caps.handback.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 自定义 T4 文本转换
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本模板是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的一种功能，使用该功能可以通过转换过程来生成程序代码或其他文本文件。  使用 [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]，您可通过自定义文本模板指令处理器或文本模板宿主来扩展默认模板转换过程。  
  
## 本节内容  
 [文本模板转换过程](../modeling/the-text-template-transformation-process.md)  
 描述文本转换的工作方式，并说明模板宿主和指令处理器的作用。  
  
 [创建自定义 T4 文本模板指令处理器](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 指令处理器处理模板中的指令，如 `<#@template#>.`。该处理器在模板的编译过程中运行，可以加载程序集和其他资源。  还可插入会在运行时加载资源的代码。  通过定义自己的指令处理器，可以降低模板的复杂性。  
  
 [在 VS 扩展中调用文本转换](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 如果要编写菜单命令或事件处理程序等 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展，则您的扩展可以使用文本模板化服务来转换任何文本模板。  可以使用 Session 对象将参数数据传入模板，并使用 `<#@parameter#>` 指令从模板内获取值。  
  
 [使用自定义宿主处理文本模板](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 执行文本模板的代码时，宿主提供对外部文件以及应用程序状态的访问。  例如，在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中运行文本转换的宿主可提供对解决方案资源管理器的访问。  宿主还会在错误消息窗口中显示错误。  如果要在不同的上下文中运行文本转换，则可以定义自己的宿主，从而提供对该上下文中可用服务的访问。  
  
 如果要编写 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展，请考虑使用现有的文本转换服务而不是编写您自己的宿主。  有关更多信息，请参见[在 VS 扩展中调用文本转换](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## 参考  
 [编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)  
  
 提供文本模板指令和控制块的语法。