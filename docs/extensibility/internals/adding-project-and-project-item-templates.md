---
title: "添加项目和项目项模板 | Microsoft Docs"
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
  - "项目 [Visual Studio SDK] 添加"
  - "添加项目项 [Visual Studio]"
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 添加项目和项目项模板
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在创建时将拥有项目类型，使用标准 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(ide\) 对话框，您必须提供添加新项目和项目项 \(IDE\)支持。  下列主题讨论了如何添加项目和项目项的不同技术。  
  
## 本节内容  
 [项目上下文](../../extensibility/internals/project-context.md)  
 解释该项目为什么提供大多数上下文信息在环境中蒸发。  
  
 [项目优先级](../../extensibility/internals/project-priority.md)  
 解释项目项通常是帮助一个项目的成员避免项目用于打开项目的多义性。  
  
 [杂项文件项目](../../extensibility/internals/miscellaneous-files-project.md)  
 提供有关可用来打开文件在项目，并且该角色该项目在确定编辑的两种类型的信息时使用的要在编辑器中打开项目项。  
  
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)  
 解释什么时，会发生 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目创建。  
  
 [将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 解释添加的项的处理。 **添加新项目** 对话框。  
  
 [将目录添加到新建项目对话框](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 提供签入包含用于自定义的模板使 VSPackage 的目录的示例。  
  
 [添加目录更改为添加新项对话框](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 为 **添加新项目** 对话框提供注册新的示例将目录。  
  
 [IDE 定义用于扩展项目系统的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 列出命令项目的不同类型用于扩展项目系统使用的。  
  
 [通常用于扩展项目的对象的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 列出用于扩展 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 项目系统的对象的 CATIDs。  
  
## 相关章节  
 [如何: 打开特定于项目的编辑器](../../extensibility/how-to-open-project-specific-editors.md)  
 提供打开内部绑定的项目的分步说明将项目的特定版本。  
  
 [如何: 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)  
 提供打开标准编辑器的分步说明。  
  
 [项目子类型](../../extensibility/internals/project-subtypes.md)  
 提供指向项目子类型概念性主题。  项目子类型扩展现有 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 项目。  
  
 [项目类型](../../extensibility/internals/project-types.md)  
 提供指向提供有关如何的信息设计新项类型的其他主题的链接。