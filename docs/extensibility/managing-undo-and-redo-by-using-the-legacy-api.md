---
title: "管理撤消和重做通过旧版 API |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41672845d318707512472f556753f429661d008c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>管理撤消和重做通过旧版 API
编辑器必须支持使用户可以反向他们最近的更改，当它们修改代码时的撤消操作。 在实现的大多数编辑器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可以撤消支持自动提供的集成的开发环境 (IDE)。  
  
## <a name="in-this-section"></a>本节内容  
 [如何： 实现撤消管理](../extensibility/how-to-implement-undo-management.md)  
 与一个或多个视图为编辑器提供恢复数据的功能。  
  
 [如何： 清除撤消堆栈](../extensibility/how-to-clear-the-undo-stack.md)  
 说明如何清除撤消堆栈。  
  
 [如何： 使用链接的撤消管理](../extensibility/how-to-use-linked-undo-management.md)  
 将链接的撤消管理合并到你的编辑器。  
  
## <a name="reference"></a>参考  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 提供一个编辑器，支持多个视图的撤消管理。  
  
## <a name="related-sections"></a>相关章节