---
title: "源控制集成 Essentials | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Essentials 的源代码管理集成"
  - "源代码管理集成概述"
  - "essentials 的服务器，源代码管理集成"
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 源控制集成 Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持源代码管理集成的两种类型:提供了基本功能和使用编译源代码管理插件 API 的源代码管理插件 \(以前称为 MSSCCI API\) 和提供更强大的功能的基于 VSPackage 的源代码管理集成解决方案。  
  
## 源代码管理插件  
 源代码管理插件编写为实现源代码管理插件 API 的 DLL。  注册和源代码管理集成功能通过 API 提供。  此方法比源代码管理 VSPackage 很容易实现，并且，对于大多数源代码管理操作 \(UI\)使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 用户界面。  
  
 使用源代码管理插件 API，若要实现源代码管理插件，请执行以下步骤:  
  
1.  创建实现在 [源代码管理插件](../../extensibility/source-control-plug-ins.md)指定的函数的 DLL。  
  
2.  注册 DLL 进行适当的注册表项，如 [如何: 安装了源代码管理插件](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)所述。  
  
3.  创建一个帮助器 UI 并显示，而提示按源控件适配器包 \( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 元素处理源代码管理功能通过源代码管理插件\)。  
  
 有关更多信息，请参见 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)。  
  
## 源代码管理 VSPackage  
 源代码管理 VSPackage 实现允许您开发 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 源代码管理的 UI 自定义的替代。  此方法提供对源代码管理集成的完全控制，但是，它需要提供 UI 元素和实现会提供一个插件方法下的源代码管理接口。  
  
 若要实现源代码管理 VSPackage，必须:  
  
1.  创建和注册拥有源代码管理 VSPackage，如 [注册和所选内容](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)所述。  
  
2.  创建一个自定义 UI 替换默认的数据源控件 UI。  请参见 [自定义用户界面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。  
  
3.  指定标志符号将使用的和处理 **解决方案资源管理器** 标志符号事件。  请参见 [标志符号控件](../../extensibility/internals/glyph-control-source-control-vspackage.md)。  
  
4.  如 [保存的查询编辑查询](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)所示，处理查询编辑器并查询保存操作，。  
  
 有关更多信息，请参见 [创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
## 请参阅  
 [概述](../../extensibility/internals/source-control-integration-overview.md)   
 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)