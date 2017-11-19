---
title: "确定是否实现源控件 VSPackage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 808f2fda26046962eada377f8a204351adef19bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>确定是否实现源控件 VSPackage
本部分用于扩展源代码管理解决方案，并提供有关选择合适的集成路径的综合性准则为基础进行阐述的源控件插件和源代码管理 Vspackage 的选择。  
  
## <a name="small-source-control-solution-with-limited-resources"></a>资源有限的小源代码管理解决方案  
 如果你具有有限的资源，并且不能承受编写源代码管理包的开销，你可以创建基于源控制插件 API 的插件。这使您可以与源代码管理包，并行工作，并且可以切换源控件插件和按需包之间。 有关详细信息，请参阅[注册和选择](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>使用一套丰富功能集的大型源代码管理解决方案  
 如果你想要实现提供充分不捕获通过使用源控件插件 API 的丰富的源控件模型的源控制解决方案，你可以为集成路径考虑源代码管理包。 尤其是当如此，而是将替换 （了源控件插件与通信并提供一个基本的源控件 UI） 的源控件适配器包替换为你自己，以便你可以在自定义方式中处理的源控件事件。 如果你已有对令人满意的源控制 UI 和想要保留在该体验[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，源代码管理包选项使你能够实现就是这样。 源代码管理包不是泛型，旨在仅用于使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 如果你想要实现提供灵活性，并更丰富控制的源控制逻辑和 UI 源代码管理解决方案，你可能更喜欢源控件包集成路由。 你可以：  
  
1.  注册您自己的源代码管理 VSPackage (请参阅[注册和选择](../../extensibility/internals/registration-and-selection-source-control-vspackage.md))。  
  
2.  将替换为你的自定义 UI 的默认源控件 UI (请参阅[自定义用户界面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md))。  
  
3.  指定字形来使用和处理解决方案资源管理器标志符号事件 (请参阅[标志符号控件](../../extensibility/internals/glyph-control-source-control-vspackage.md))。  
  
4.  处理查询编辑和保存查询事件 (请参阅[查询编辑查询保存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md))。  
  
## <a name="see-also"></a>另请参阅  
 [创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)