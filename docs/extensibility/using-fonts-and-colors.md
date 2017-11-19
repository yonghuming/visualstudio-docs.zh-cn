---
title: "使用字体和颜色 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ce64c7cac36319d1e55efb0ddf2216dc218805c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-fonts-and-colors"></a>使用字体和颜色
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]向使用字体和颜色显示文本提供支持。  
  
## <a name="in-this-section"></a>本节内容  
 [字体和颜色概述](../extensibility/font-and-color-overview.md)  
 讨论中的文本字体和颜色设置[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)。 此外介绍了的类别和显示项的概念并描述了 Vspackage 和核心编辑器如何使用文本特性。  
  
 [获取字体和文本着色的颜色信息](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 提供的指南在管理的 Vspackage 中实现文本着色**类别**以外**文本编辑器**。  
  
 [访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)  
 说明如何当前字体和颜色设置可以存储、 检索和应用。  
  
 [实现自定义类别和显示项](../extensibility/implementing-custom-categories-and-display-items.md)  
 介绍的基本步骤依据一个窗口可以创建和使用其自己的**显示项**和**类别**以支持文本显示。  
  
 此方法要求 VSPackage 来实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>接口和相关的接口。  
  
 [如何： 访问的内置的字体和配色方案](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 讨论如何定义和通过使用内置的字体和颜色，注册某一类别和启动使用系统提供的字体和颜色。  
  
## <a name="reference"></a>参考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 提供的实例`IVsFontAndColorDefaults`或<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>对应于中列出的特定项的接口**设置显示属于**列入**字体和颜色**页**选项**对话框。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 使 VSPackage 来支持 IDE**字体和颜色**页上通过定义默认字体和颜色的窗口或 UI 组件。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 提供一种机制，通过它提供字体和颜色支持可以指定显示项组-表示两个或多个类别的联合的超类别的 VSPackage。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 使 VSPackage 来检索字体和颜色数据，或将其保存到注册表。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 通知字体和颜色设置中使用更改的字体和颜色信息的 Vspackage。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 提供工具使用的方法所用的输入和输出数据的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**字体和颜色**机制。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 控件的字体和颜色设置的缓存。  
  
## <a name="related-sections"></a>相关章节  
 [开发旧版语言服务](../extensibility/internals/developing-a-legacy-language-service.md)  
 讨论 Vspackage 如何使用语言服务以自定义[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]编辑器。  
  
 [自定义编辑器中的语法着色](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 如何[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]编辑器使用语言服务实现语法着色。  
  
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 说明如何使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]服务来创建匹配的其余部分的 UI 元素[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。