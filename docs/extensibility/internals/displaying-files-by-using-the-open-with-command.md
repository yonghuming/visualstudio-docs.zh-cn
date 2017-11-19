---
title: "通过使用命令打开显示文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed8a19ce0cfb6a7936d61ff7a5855498d2010359
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-files-by-using-the-open-with-command"></a>通过使用命令打开显示文件
一个项目可以要求 IDE 以显示**打开**对话框。 此请求将提示用户打开具有选定的标准编辑器的文件。 以下步骤介绍了此过程。  
  
1.  项目调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，指定一个值为 OSE_UseOpenWithDialog`OSEOpenDocEditor`参数。  
  
2.  根据文档的文件扩展名，IDE 确定注册表可以中列出的编辑器打开指定的文档并显示此信息的**打开**对话框。  
  
    > [!NOTE]
    >  具有一个内部函数的编辑器，必须包括在项目**打开**对话框中必须为每个此类编辑器注册编辑器工厂。 内部函数编辑器仅函数以及特定类型的项目，在实现中的强制执行<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。 IDE 提供了针对核心文本编辑器和二进制编辑器的内置编辑器工厂。 IDE 还创建代表每个已注册的 Windows 文件关联的编辑器工厂的实例。 此类文件的一个示例是 Microsoft Word。  
  
3.  用户选择中的一个项时，就会立即**打开**对话框中，IDE 然后通过调用打开文档<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。 有关详细信息，请参阅[如何： 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)。  
  
## <a name="see-also"></a>另请参阅  
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)   
 [通过使用打开文件命令显示文件](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [如何：打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)