---
title: "标志符号控件 (源控件 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac7839d4d7456f28d7e4b5b8ecd4096904dce38e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="glyph-control-source-control-vspackage"></a>标志符号控件 (源控件 VSPackage)
可用于源代码管理 Vspackage 深度集成的一部分是能够显示其自己的标志符号，以指示在源代码管理下的项的状态。  
  
## <a name="levels-of-glyph-control"></a>标志符号控制级别  
 状态标志符号是一个图标，指示时显示，例如，在某个项的当前状态**解决方案资源管理器**或**类视图**。 源代码管理 VSPackage 可以执行两个级别的标志符号控件。 这样做可以防止到一组预定义的标志符号提供的标志符号的选择[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE，也可以定义一组自定义要显示的标志符号。  
  
### <a name="default-set-of-glyphs"></a>组默认的标志符号  
 若要确定与中的项相关联的状态标志符号**解决方案资源管理器**，项目从源控件使用请求的状态标志符号<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>。 源代码管理 VSPackage 可能会决定要保留的限于由 IDE 提供的预定义标志符号的标志符号的选择。 在这种情况下，VSPackage 传递回去表示在 vsshell.idl 中定义的标志符号枚举的值的数组。 有关详细信息，请参阅<xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>。这是一组预定义的设置的 IDE，如"签入"标志符号，以及一个复选标记为"已签出"标志符号挂锁的标志符号。  
  
### <a name="custom-set-of-glyphs"></a>自定义设置的标志符号  
 源代码管理 VSPackage 时能够使用其自己的标志符号进行获得唯一的"外观和感觉"安装它。 在一个新的源控件 VSPackage 处于活动状态，它应为可以开始使用其自己的标志符号即使以往源控制 VSPackage 仍加载，但处于非活动状态。 在此模式下，VSPackage 的源控件仍可使用现有的图标以便保持查看与一致[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如果它选择。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服务支持的接口， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>，而后者 VSPackage 可以选择实现并将通过 IDE 的要求。 当 IDE 发出请求，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]反过来将尝试从当前已注册的源代码管理 VSPackage 中获取此接口。 如果该接口存在于已注册的 VSPackage，自定义标志符号的 IDE 的请求成功;否则为[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 使用其默认组的标志符号。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>方法由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]为了获取显示各种源控件的图像列表的状态。 源代码管理 VSPackage IDE 返回其自定义标志符号的图像列表的句柄。 IDE 此时生成的图像列表的副本，并更高版本使用它来选择要显示的标志符号。 如果不支持的新接口或`IVsSccGlyphs::GetCustomGlyphList`方法返回 E_NOTIMPL，则 IDE 从提供的标志符号的默认列表中获取其标志符号[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>