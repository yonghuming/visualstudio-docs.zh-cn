---
title: "通过使用打开文件命令显示文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2cbcb6e6239552ae32c817601634587a2fe3a41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>通过使用打开文件命令显示文件
以下步骤描述了 IDE 如何处理**打开的文件**命令，可在找到**文件**菜单中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 步骤还介绍项目应如何响应来自此命令的调用。  
  
 当用户单击**打开的文件**命令**文件**菜单上，并选择文件从**打开的文件**对话框中，将发生以下过程。  
  
1.  使用正在运行的 document 表，IDE 确定文件是否已在项目中打开。  
  
    -   如果文件处于打开状态，则 IDE 将 resurfaces 窗口。  
  
    -   如果该文件未打开，IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>查询来确定哪些项目可以打开的文件的每个项目。  
  
        > [!NOTE]
        >  中的项目实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>，提供一个优先级值，指示你的项目将打开文件的级别。 中提供了优先级值<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>枚举。  
  
2.  每个项目具有优先级级别，用于指示重要性响应它会将放置于的项目以打开该文件。  
  
3.  IDE 使用以下条件来确定哪些项目中打开的文件：  
  
    -   将使用最高优先级 (DP_Intrinsic) 进行响应的项目打开的文件。 如果多个项目具有此优先级响应，响应的第一个项目打开的文件。  
  
    -   如果具有最高优先级 (DP_Intrinsic) 没有项目进行响应，但使用的相同，较低优先级的所有项目响应，活动的项目将打开的文件。 如果没有项目处于活动状态，以响应的第一个项目打开的文件。  
  
    -   如果没有项目声明 (DP_Unsupported) 的文件的所有权，杂项文件项目打开的文件。  
  
         如果创建杂项文件项目的实例，则项目始终通过值 DP_CanAddAsExternal 做出响应。 此值指示项目可以打开的文件。 使用此项目以容纳打开的文件不在任何其他项目。 此项目中的项列表不被永久性;此项目是在中可见**解决方案资源管理器**仅当它用于打开文件。  
  
         杂项文件项目并不表示它可以打开的文件，如果尚未创建项目的实例。 在这种情况下，IDE 将创建杂项文件项目的实例并通知项目打开的文件。  
  
4.  只要 IDE 确定哪些项目中打开的文件，它调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>，在项目的方法。  
  
5.  然后，该项目包含通过使用特定于项目的编辑器或标准编辑器打开文件的选项。 有关详细信息，请参阅[如何： 打开项目特定编辑器](../../extensibility/how-to-open-project-specific-editors.md)和[如何： 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)分别。  
  
## <a name="see-also"></a>另请参阅  
 [通过使用命令打开显示文件](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 打开项目特定编辑器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何：打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)