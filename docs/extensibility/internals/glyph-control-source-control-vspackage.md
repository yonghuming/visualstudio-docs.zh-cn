---
title: "标志符号控件 (源控制 VSPackage) | Microsoft Docs"
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
  - "标志符号，源代码管理包"
  - "源代码管理包，标志符号"
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 标志符号控件 (源控制 VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

一部分的深入的集成可用于源代码管理 Vspackage 是能够显示它们的标志符号指示项的状态在源代码管理。  
  
## 标志符号控件的级别  
 状态标志符号是指示项的当前状态，同时显示，例如在 **解决方案资源管理器** 或在 **类视图**的图标。  源代码管理 VSPackage 中执行标志符号控件的两个级别。  它可以限制到预定义的标志符号选择 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 提供的设置标志符号，也可以定义自定义要显示的设置标志符号。  
  
### 默认设置标志符号  
 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>，确定与 **解决方案资源管理器**的项的状态标志符号，项目请求从源代码管理的状态标志符号。  源代码管理 VSPackage 可能决定保留标志符号选择绑定到 IDE 提供的预定义的标志符号。  在这种情况下， VSPackage 将表示在 vsshell.idl 定义的标志符号枚举的值。  有关更多信息，请参见 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> 。这是预定义 IDE 中设置标志符号，如 “签入”标志符号的挂锁和复选标记， “签出”标志符号。  
  
### 自定义设置标志符号  
 ，在安装时，源代码管理 VSPackage 中为单个 “外观”使用自己的标志符号它。  如果新的源代码管理 VSPackage 处于活动状态时，应可以开始使用自己的标志符号，即使以前源代码管理 VSPackage 仍会加载，但非活动。  在此模式下，则为; 如果选择，源代码管理 VSPackage 仍可以使用现有的图标以维护看起来一致。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 服务支持接口， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>， VSPackage 可以选择实现，并将请求由 IDE。  当 IDE 发出请求， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fprintf 又会尝试获取从当前注册的源代码管理 VSPackage 的此接口。  如果接口存在于注册的 VSPackage， IDE 的需要自定义标志符号成功;否则， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 使用的默认设置标志符号。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 用于 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> 方法获取显示各种数据源控件状态的图像列表。  源代码管理 VSPackage 回图像的句柄提供了自定义标志符号列表的 IDE。  IDE 副本图像此时列表并随后使用它选择标志符号显示。  如果新接口或不支持 `IVsSccGlyphs::GetCustomGlyphList` 方法返回 E\_NOTIMPL，则 IDE 从默认获取其标志符号 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的列表标志符号。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>