---
title: "优化菜单和工具栏命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令 [Visual Studio] 菜单"
  - "工具栏的命令 [Visual Studio]"
  - "菜单 [Visual Studio SDK] 命令"
  - "实现菜单命令"
  - "工具栏 [Visual Studio] 命令"
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 优化菜单和工具栏命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vspackage 和到其相应命令添加 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可能会导致很拥挤的 UI。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供了方法，以帮助最小化 UI 命令混淆。  
  
## 本节内容  
 [提供命令](../../extensibility/internals/making-commands-available.md)  
 提供有关最小化围的通用准则 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI 时添加 Vspackage。  
  
 [放置指导原则](../../extensibility/internals/command-placement-guidelines.md)  
 提供用于实现根据命令集的大小的 VSPackage 的特定指导原则。  
  
## 相关章节  
 [命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)  
 说明如何创建一个用户界面，包括菜单、 工具栏和命令组合框。