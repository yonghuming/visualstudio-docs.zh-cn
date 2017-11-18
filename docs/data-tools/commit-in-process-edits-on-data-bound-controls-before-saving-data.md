---
title: "在保存数据前提交数据绑定控件上的中正在编辑 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 191206e9cc16271e64abbeaba87d86ac0108924b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>在保存数据前提交数据绑定控件上的进程内编辑
当编辑数据绑定控件中的值，用户必须关闭当前的记录，以将更新后的值提交到该控件绑定到基础数据源中导航。 当拖动项时从[数据源窗口](add-new-data-sources.md)拖到窗体，拖放的第一项生成的代码插入**保存**按钮单击事件的<xref:System.Windows.Forms.BindingNavigator>。 此代码调用<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法<xref:System.Windows.Forms.BindingSource>。 因此，调用<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法生成仅为第一个<xref:System.Windows.Forms.BindingSource>，它将添加到窗体。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A>调用将提交在过程中，当前正在编辑的任何数据绑定控件中的任何更改。 因此，如果数据绑定控件仍然具有焦点并且单击**保存**按钮，所有挂起的编辑，因为在执行真正的保存之前提交事务，控件 (`TableAdapterManager.UpdateAll`方法)。  
  
 你可以配置应用程序以自动提交更改，即使用户尝试保存数据，而不保存的一部分提交所做的更改，过程。  
  
> [!NOTE]
>  设计器添加`BindingSource.EndEdit`代码仅为第一个项目拖放到窗体。 因此，你必须添加要调用的代码行<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法为每个<xref:System.Windows.Forms.BindingSource>窗体上。 你可以将手动添加代码行以调用<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法为每个<xref:System.Windows.Forms.BindingSource>。 或者，可以添加`EndEditOnAllBindingSources`到窗体的方法，在执行保存之前调用它。  
  
 下面的代码使用[LINQ （语言集成查询）](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)查询以循环访问所有<xref:System.Windows.Forms.BindingSource>组件和调用<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法为每个<xref:System.Windows.Forms.BindingSource>窗体上。  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>若要调用 EndEdit 的窗体上的所有 BindingSource 组件  
  
1.  将以下代码添加到窗体包含<xref:System.Windows.Forms.BindingSource>组件。  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  添加以下调用以保存该窗体的数据的紧前面的代码行 (`TableAdapterManager.UpdateAll()`方法):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [分层更新](../data-tools/hierarchical-update.md)