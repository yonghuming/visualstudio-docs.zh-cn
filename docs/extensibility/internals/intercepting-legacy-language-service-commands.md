---
title: "截获旧语言服务命令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73524ce47dfea2d30e44e51e97bf584a95a86482
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="intercepting-legacy-language-service-commands"></a>截获旧语言服务命令
与[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，你可以将否则处理文本视图语言服务截距命令。 这可用于文本视图不管理的特定于语言的行为。 可以通过将一个或多个命令筛选器添加到文本视图中，从你的语言服务截获这些命令。  
  
## <a name="getting-and-routing-the-command"></a>获取和路由命令  
 命令筛选器是<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>监视某些字符序列或命令的对象。 你可以将多个命令筛选器关联的单个文本视图。 每个文本视图维护命令链筛选器。 创建新的命令筛选器后，你将筛选器添加到相应的文本视图的链。  
  
 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>将命令筛选器添加到该链。 当调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]返回可以将命令筛选器不处理的命令传递到另一个命令筛选器。  
  
 可以使用以下选项用于命令处理：  
  
-   处理命令，然后将该命令到下一个命令筛选器传递链中。  
  
-   处理命令并不传递到下一个命令筛选器的命令。  
  
-   不处理命令，但传递到下一个命令筛选器的命令。  
  
-   忽略该命令。 不处理它在当前筛选器，并不将其传递到下一个筛选器。  
  
 语言服务应处理哪些命令有关的信息，请参阅[语言服务筛选器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。