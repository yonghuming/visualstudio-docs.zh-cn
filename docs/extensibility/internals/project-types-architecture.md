---
title: "项目类型体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86ff1ed0b616eb52d57755e7537642e4f086c1f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-types-architecture"></a>项目类型体系结构
本部分包含有关体系结构中的项目类型的详细的信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="in-this-section"></a>本节内容  
 [项目模型的元素](../../extensibility/internals/elements-of-a-project-model.md)  
 列出了可以使用一种项目类型的服务和它必须实现的接口。  
  
 [项目模型核心组件](../../extensibility/internals/project-model-core-components.md)  
 描述项目类型都必须实现和 （可选） 可实现以提供其他功能的接口。  
  
 [何时创建项目类型](../../extensibility/internals/when-to-create-project-types.md)  
 帮助你决定时必须创建一个项目类型，当您可以使用另一个[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如 Vspackage 和编辑器来实现相同的目的的扩展性功能。  
  
 [层次结构和选择](../../extensibility/internals/hierarchies-and-selection.md)  
 描述如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用层次结构和选择上下文提供一致和简化用户体验。  
  
## <a name="related-sections"></a>相关章节  
 [项目子类型](../../extensibility/internals/project-subtypes.md)  
 说明如何项目子类型允许你自定义的项目系统的行为[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]。  
  
 [项目类型](../../extensibility/internals/project-types.md)  
 基本的构建块的形式提供的项目概述[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)。 提供了指向解释如何项目控制生成和编译代码的其他主题的链接。