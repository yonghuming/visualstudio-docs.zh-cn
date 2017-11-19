---
title: "开始使用源控件插件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ccbc7536a899226b7f2d9433b6c451df33bbde5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-source-control-plug-ins"></a>开始使用源控件插件
若要创建源代码管理插件，必须创建一个 DLL，它实现在源控件插件 API 中，定义的函数，然后注册与 DLL[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以使其在源代码版本控制中可供使用。  
  
 为源控件插件提供了三个版本的源控制插件 API （版本 1.1、 1.2 和 1.3）。以下网页中介绍的源控件插件 API 是 1.3 版。 它的设计目标是与源代码控制插件完全兼容支持 1.1 和 1.2 的版本。 [What's New in 源控件插件 API 版本 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)部分将详细介绍支持的源控制插件 API 的最新版本的新功能。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：安装源代码管理插件](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 描述如何使在源代码管理 DLL 中插入所需的注册表项。  
  
 [源代码管理插件 API 版本 1.3 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 提供对源控件插件 API 版本 1.3 中所做的更改的简要概述。  
  
 [源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 提供对源控件插件 API 版本 1.2 中所做的更改的简要概述。  
  
## <a name="related-sections"></a>相关章节  
 [源代码管理插件](../../extensibility/source-control-plug-ins.md)  
 提供源控制插件 API 中的所有元素的完整的列表。  
  
 [创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 定义源控件插件 SDK 并描述包含的资源。