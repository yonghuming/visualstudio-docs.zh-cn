---
title: "支持的源控件 | Microsoft Docs"
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
  - "源控件 [Visual Studio SDK] 支持"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 支持的源控件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持文件签出、签入和其他源代码管理操作的一个项或编辑。  作为源代码管理客户端， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 旨在与受源代码管理包进行交互，例如 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]，提供存档，版本控制和的动态定义的控件工具设置文件。  
  
## 本节内容  
 [源代码管理包的模型](../../extensibility/internals/model-for-source-control-packages.md)  
 描述项类型必须实现支持源代码管理的接口。  
  
 [设计决策](../../extensibility/internals/source-control-design-decisions.md)  
 提供答案更改的问题如何实现一种项目类型。  
  
 [配置的详细信息](../../extensibility/internals/source-control-configuration-details.md)  
 描述支持源代码管理如何更改项目类型的实现。  
  
 [项目和编辑器的其他准则](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 讨论项目类型和编辑的最佳做法。  
  
 [运行时详细信息](../../extensibility/internals/source-control-runtime-details.md)  
 ，当用户将其添加到源代码管理系统时，介绍如何在中注册一个项目。  
  
## 参考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 指示到环境或源代码控制包文件会更改在内存或保存。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 向项目和层次结构注册与源代码并获取有关源代码管理状态的信息。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 实现在项目系统为项目文件和项目项提供源代码管理。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 用于使项查询权限的环境中添加，请删除或重命名文件或目录重命名解决方案。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 请注意对项目文件或目录更改的客户端。  
  
## 相关章节  
 [项目类型](../../extensibility/internals/project-types.md)  
 ，在基本构造块 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成开发环境，提供项目的概述。 \(IDE\)  提供指向解释如何在项目控件生成和编译代码的其他主题的链接。