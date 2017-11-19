---
title: "源控制集成 Essentials |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 09e96719bd7d9a2091bf31dc343036f0312c02fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-integration-essentials"></a>Essentials 源控件的集成
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支持两种类型的源代码管理集成： 提供基本功能，并使用源控件插件 API （前称 MSSCCI API） 和一个基于 VSPackage 的源控制集成解决方案生成了源代码管理插件，提供更强大的功能。  
  
## <a name="source-control-plug-in"></a>源代码管理插件  
 源代码管理插件编写为 DLL 实现源控制插件 API。 注册和源控件集成功能提供通过 API。 这种方法是更轻松地实现都比源代码管理 VSPackage，并使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]大多数源代码管理操作的用户界面 (UI)。  
  
 若要实现源代码管理插件使用源控件插件 API，请按照下列步骤：  
  
1.  创建实现中指定的函数的 DLL[源代码管理插件](../../extensibility/source-control-plug-ins.md)。  
  
2.  中所述，通过进行相应的注册表项注册 DLL[如何： 安装源代码管理插件](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)。  
  
3.  创建帮助器 UI，并将其通过源代码管理适配器包出现提示时显示 ([!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]处理源控件插件通过源代码管理功能的组件)。  
  
 有关详细信息，请参阅[创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)。  
  
## <a name="source-control-vspackage"></a>源控件 VSPackage  
 源代码管理 VSPackage 实现允许你开发的自定义的替换[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]源代码管理 UI。 此方法提供了对源代码管理集成的完全控制，但需要你提供的 UI 元素，并实现否则将下的插件方法提供的源控件接口。  
  
 若要实现源代码管理 VSPackage，你必须：  
  
1.  创建并注册 VSPackage，你自己源代码管理中所述[注册和选择](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
2.  将替换为你的自定义 UI 默认的源代码管理 UI。 请参阅[自定义用户界面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。  
  
3.  指定要使用，并处理标志符号**解决方案资源管理器**标志符号事件。 请参阅[标志符号控件](../../extensibility/internals/glyph-control-source-control-vspackage.md)。  
  
4.  处理查询编辑和保存查询事件中所示[查询编辑查询保存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)。  
  
 有关详细信息，请参阅[创建源控件 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
## <a name="see-also"></a>另请参阅  
 [概述](../../extensibility/internals/source-control-integration-overview.md)   
 [创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [创建源代码管理 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)