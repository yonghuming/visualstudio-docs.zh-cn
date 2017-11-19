---
title: "通过使用旧版 API 更改查看设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe5bd3b149981ca8183e9311185ef5d6ed19e48f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>通过使用旧版 API 更改视图设置
通过用户时可以更改设置核心编辑器功能，如自动换行、 选定内容的边距和虚拟空间**选项**对话框。 但是，还有可能要更改这些设置以编程方式。  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>通过使用旧版 API 更改设置  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>接口公开一组文本编辑器属性。 文本视图包含表示文本视图以编程方式更改的设置的组的属性 (GUID_EditPropCategory_View_MasterSettings) 的类别。 一旦已以这种方式更改查看设置，它们不能更改在**选项**对话框中，直到它们被重置。  
  
 以下是用于更改核心编辑器的一个实例的视图设置的典型过程。  
  
1.  调用`QueryInterface`上 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) 为<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>接口。  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>方法，指定一个值为 GUID_EditPropCategory_View_MasterSettings`rguidCategory`参数。  
  
     执行此操作返回一个指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>接口，其中包含的视图的强制属性集。 永久强制此组中的任何设置。 如果设置不在此组中，则它将遵循中指定的选项**选项**对话框中或用户的命令。  
  
3.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>方法，指定中的适当的设置值`idprop`参数。  
  
     例如，若要强制自动换行，请调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>并指定值的 VSEDITPROPID_ViewLangOpt_WordWrap，`vt`为`idprop`参数。 在此调用中，`vt`是变体类型 VT_BOOL 和`vt.boolVal`是 VARIANT_TRUE。  
  
## <a name="resetting-changed-view-settings"></a>重置已更改的视图设置  
 若要重置设置核心编辑器的一个实例为任何已更改的视图，请调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>方法并指定中的适当的设置值`idprop`参数。  
  
 例如，若要允许自动换行自由浮动，你将它从类别中删除属性通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>并指定一个值为 VSEDITPROPID_ViewLangOpt_WordWrap`idprop`参数。  
  
 若要在一次删除所有更改的设置核心编辑器，将值指定为 VSEDITPROPID_ViewComposite_AllCodeWindowDefaults，为 vt`idprop`参数。 在此调用中，vt 是变体类型 VT_BOOL 和 vt.boolVal 是 VARIANT_TRUE。  
  
## <a name="see-also"></a>另请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [通过使用旧版 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [“选项”对话框](../ide/reference/options-dialog-box-visual-studio.md)