---
title: "对嵌套项目的筛选 AddItem 对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "筛选嵌套的项目"
  - "嵌套的项目，AddItem 对话框框中筛选"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 对嵌套项目的筛选 AddItem 对话框
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当显示嵌套项目的某 **AddItem** 对话框，父项目可以控制项显示在对话框中。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 接口可以筛选在 **AddItem** 对话框的节点。  当子项显示 **AddItem** 对话框时，父级可以实现 `IVsFilterAddProjectItemDlg` 接口和筛选子表中的项目会显示的项。  
  
 当项目是在特定于父项目之下的功能分组，可以实现 `IVsFilterAddProjectItemDlg` ，当用户在快捷菜单上选择 **添加项目项** 在嵌套的项。  实现 `IvsFilterAddProjectItemDlg displays` 只项目特定的项目或的文件到该组。  其他组的项目项筛选对话框，因此，即使它们在同一目录中。  
  
 当用户打开子级时 **AddItem** 对话框中， `IVsFilterAddProjectItemDlg` 接口的父项目实现。  
  
 `IVsFilterAddProjectItemDlg` 接口可以按类别还实现筛选。  有关更多信息，请参见[将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)和 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)