---
title: "通过使用命令打开显示文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目类型中，支持打开 With 命令"
  - "打开命令"
  - "持久性、 支持打开 With 命令"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 通过使用命令打开显示文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目可以请求 IDE 显示 **打开。** 对话框。  此请求提示用户打开具有标准编辑选择的文件。  以下步骤介绍此过程。  
  
1.  该项调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，指定 OSE\_UseOpenWithDialog 的值。 `OSEOpenDocEditor` 参数。  
  
2.  根据文档的文件扩展名， IDE 确定在注册表中列出的哪些编辑器中打开指定文档并显示在 **打开。** 对话框的此信息。  
  
    > [!NOTE]
    >  有一个内部编辑在 **打开。** 对话框必须包括的项目必须注册每个这样的编辑的版本工厂。  内部编辑器与项目一起的特定参数的函数，在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 方法的实现强制实施。  IDE 提供核心文本编辑器和二进制编辑器的内置编辑工厂。  IDE 键入每注册窗口文件关联来创建编辑工厂的实例。  此类文件的示例是 Microsoft Word。  
  
3.  当用户选择一个项目。 **打开。** 对话框， IDE 然后通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法打开文档。  有关更多信息，请参见 [如何: 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)。  
  
## 请参阅  
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)   
 [通过使用打开文件命令显示文件](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [如何: 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)