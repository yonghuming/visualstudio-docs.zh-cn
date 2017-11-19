---
title: "VSTextView 对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3b7cdc698a169150560b2a924cd6f3317fa78ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vstextview-object"></a>VSTextView 对象
文本视图是一个窗口，允许用户查看和编辑文本缓冲区的 Unicode 文本。 从根本上来说，该视图是大多数用户所称为的编辑器。 由于各种文本层 （自动换行、 大纲显示文本等） 的情况下，该视图从缓冲区分开的视图不保证可精确地表示的缓冲区中的文本。 有关文本视图的详细信息，请参阅[使用旧版 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 下表显示中的在接口<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>对象。  
  
|接口|描述|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|标准 OLE 接口。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|标准 OLE 接口。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|标准 OLE 接口。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|标准 OLE 接口。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|允许创建复合操作 （即，在单个撤消/重做单元进行分组的操作）。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|用于管理和访问视图中提供的基本方法。 `IVsTextView`不是线程安全的。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|创建和管理窗口窗格。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|与文本层交互。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|来自不同线程中执行视图上的操作。|  
  
## <a name="see-also"></a>另请参阅  
 [数字编辑](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer 对象](../extensibility/vstextbuffer-object.md)   
 [通过使用旧版 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)