---
title: "确定是否实现源控件 VSPackage | Microsoft Docs"
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
  - "源代码管理包，关于源代码管理包"
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 确定是否实现源控件 VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本节阐述源代码管理插件和源代码管理扩展的源代码管理解决方案的 Vspackage 选择并提供有关选择适当的集成路径的全面的指南。  
  
## 使用有限资源的小型源控制解决方案  
 如果您具有有限资源，并且不能负担开销编写源代码管理包，可以创建源代码管理插件基于 API 的插件。  这使您可以并行使用源代码管理包一起使用，因此，您可以在源代码管理插件和包之间切换。要求。  有关更多信息，请参见 [注册和所选内容](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
## 设置了丰富的功能的主要源代码管理解决方案  
 如果要实现使用源代码管理插件 API，提供丰富的源控件设计没有足够访问的源代码管理解决方案，您可以源代码管理包将集成路径是可见的。  这适用，尤其是在您将希望替换与通信源代码管理插件并提供一个基本的源代码管理 UI 的源控件适配器包 \(拥有，以便您可以处理源代码管理事件以自定义方式。  如果您已具有一个令人满意的源代码管理 UI 并保存在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的体验，该源代码管理包选项能让您执行此操作。  源代码管理包不是泛型和独立旨在用于 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中使用。  
  
 如果要实现提供灵活性和更丰富的控件绑定到数据源控件的逻辑和 UI 的源代码管理解决方案，您可能希望源代码管理集成包方法。  您可以：  
  
1.  注册拥有源代码管理 VSPackage \(请参见 [注册和所选内容](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)\)。  
  
2.  创建一个自定义 UI 替换默认的数据源控件 UI \(请参见 [自定义用户界面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)\)。  
  
3.  指定标志符号将使用的和处理解决方案资源管理器标志符号事件 \(请参见 [标志符号控件](../../extensibility/internals/glyph-control-source-control-vspackage.md)\)。  
  
4.  处理查询编辑器并查询保存操作 \(请参见 [保存的查询编辑查询](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)\)。  
  
## 请参阅  
 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)