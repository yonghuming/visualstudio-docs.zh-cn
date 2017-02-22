---
title: "源控制运行时详细信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理 [Visual Studio SDK]，运行时详细信息"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 源控制运行时详细信息
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目将添加到源代码管理，当用户将在项目的文件添加到源代码管理时，或通过一个自动化控制器，例如向导。  项目不为其指定它在源代码管理之下;它支持源代码管理，但是，必须手动添加到它。  
  
## 向源代码管理签入包  
 如果在项目的文件将添加到源代码管理时，环境调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> 提供可用于为 cookie 由源代码管理系统的四个不透明的字符串。  存储这些字符串在项目文件。  应将这些字符串到源代码管理存根 \(管理源代码管理包\) 的 Visual Studio 组件在项目类型的激活通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>。  这进而将相应的源代码管理包前向对其 `IVsSccManager2::RegisterSccProject`的实现。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [支持的源控件](../../extensibility/internals/supporting-source-control.md)