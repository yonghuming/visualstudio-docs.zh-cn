---
title: "使用字体和颜色 | Microsoft Docs"
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
  - "在 IDE 中控制的字体"
  - "IDE 中，控制文本的颜色和字体"
  - "字体和颜色属性页"
  - "字体和颜色的控件 [Visual Studio SDK]"
  - "文本、 IDE"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用字体和颜色
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 提供支持使用字体和颜色显示文本。  
  
## 本节内容  
 [字体和颜色概述](../extensibility/font-and-color-overview.md)  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(ide\) 讨论文本的字体和颜色设置 \(IDE\)。  介绍几种类别和显示项目的概念，并描述 Vspackage 和核心编辑器如何使用文本属性。  
  
 [获取字体和文本着色的颜色信息](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 为实现文本着色提供除 **文本编辑器**外，管理 **类** 的准则在 Vspackage。  
  
 [访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)  
 说明如何存储，检索和应用当前字体和颜色设置。  
  
 [实现自定义类别和显示项](../extensibility/implementing-custom-categories-and-display-items.md)  
 描述窗口可以创建并使用其自己 **显示项目** 和 **类** 支持文本显示的基本步骤。  
  
 此方法需要 VSPackage 实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 接口和相关接口。  
  
 [如何︰ 访问内置字体和配色方案](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 通过使用内置的字体和颜色，讨论如何定义和注册了类，并启动使用系统提供的字体和颜色。  
  
## 参考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 提供 `IVsFontAndColorDefaults` 实例或对应于 **显示设置。** 列表的特定项的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 接口。 **选项** 对话框的 **字体和颜色** 页列表。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 使 VSPackage 通过定义默认字体和颜色支持 IDE **字体和颜色** 页窗口或用户界面元素的。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 提供 VSPackage 提供字体和颜色支持可以指定显示项目组 \- 超类表示两个或多个类别联合的框架。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 使 VSPackage 检索字体和颜色数据或将其保存到注册表。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 通知使用有关更改的字体和颜色信息对字体和颜色设置上的 Vspackage。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 提供用于处理的工具。在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **字体和颜色** 结构的方法使用的输入和输出数据。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 控件字体和颜色设置缓存。  
  
## 相关章节  
 [开发语言服务](../extensibility/internals/developing-a-legacy-language-service.md)  
 讨论 Vspackage 如何使用语言服务自定义 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编辑。  
  
 [语法着色中自定义编辑器](../extensibility/syntax-coloring-in-custom-editors.md)  
 看出 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编辑器如何使用语言服务实现语法着色。  
  
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 解释如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 服务创建与其余 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的 UI 元素。