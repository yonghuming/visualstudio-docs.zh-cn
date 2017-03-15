---
title: "通过使用旧 API 更改视图设置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的更改查看设置"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 通过使用旧 API 更改视图设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

核心编辑器功能的设置，如自动换行，选择边距和虚拟空间，都可由用户更改传递 **选项** 对话框。  但是，更改这些以编程方式设置也是可能的。  
  
## 使用传统的 API 中更改设置  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 接口公开一组文本编辑器属性。  文本视图包含表示编程方式文本视图中已更改的设置组的类别特性 \(GUID\_EditPropCategory\_View\_MasterSettings\)。  对于此类更改了视图设置，它们在 **选项** 对话框无法更改，直到重置密码。  
  
 以下典型为核心编辑器的实例的更改的视图设置。  
  
1.  对 `QueryInterface` \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 接口的。  
  
2.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> 方法，指定 GUID\_EditPropCategory\_View\_MasterSettings 的值。 `rguidCategory` 参数。  
  
     执行此操作返回指向 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 接口，其中包含用来视图中强制的属性。  任何设置本组中永久是强制的。  如果设置不此组中，则将按照 **选项** 对话框或用户的命令指定的选项。  
  
3.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 方法，指定相应设置值。 `idprop` 参数。  
  
     例如，强制自动换行，请调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 并指定 VSEDITPROPID\_ViewLangOpt\_WordWrap， `idprop` 参数的 `vt` 的值。  中调用， `vt` 是类型 VT\_BOOL 变量，并 `vt.boolVal` 是 VARIANT\_TRUE。  
  
## 重置已更改的视图设置  
 若要重置设置为核心编辑器的实例的所有已更改的视图，请调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> 方法并指定相应的设置的值。 `idprop` 参数。  
  
 例如，允许自动换行自由浮动的，则从属性类别会移除它通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> 并指定 VSEDITPROPID\_ViewLangOpt\_WordWrap 的值 `idprop` 参数的。  
  
 立即若要移除核心编辑器中所有已更改的设置，请指定 VSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults 的值， `idprop` 参数的 vt。  中调用， vt 是类型 VT\_BOOL 变量，并 vt.boolVal 是 VARIANT\_TRUE。  
  
## 请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [通过使用旧 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [“选项”对话框](../ide/reference/options-dialog-box-visual-studio.md)