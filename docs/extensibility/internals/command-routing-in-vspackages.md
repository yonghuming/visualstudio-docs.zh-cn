---
title: "Vspackage 中的命令传送 | Microsoft Docs"
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
  - "路由的命令"
  - "命令传送，Visual Studio SDK"
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Vspackage 中的命令传送
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在路由命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 基于执行它的上下文。 它从向外的初始上下文传递到全局上下文。  
  
## 本节内容  
 [路由算法](../../extensibility/internals/command-routing-algorithm.md)  
 描述命令路由的解析的顺序。  
  
 [可用性](../../extensibility/internals/command-availability.md)  
 讨论命令路由。  
  
 [命令和使用互操作程序集的菜单](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 讨论托管的代码和 COM 之间路由命令中的注意事项  
  
## 相关章节  
 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)  
 讨论如何确定用户的所选内容上下文焦点的窗口上的模型。  
  
 [命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)  
 说明如何创建一个用户界面，包括菜单、 工具栏和命令组合框。