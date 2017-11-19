---
title: "如何： 打开编辑器打开文档的 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dfd145281a467a23cd01d73ff04721d68580254e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-editors-for-open-documents"></a>如何： 打开编辑器的打开的文档
项目将打开一个文档窗口之前，该项目首先必须确定文件是否已打开在另一个编辑器的文档窗口中。 文件可以在项目特定编辑器中，或者打开或使用标准编辑器之一注册[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="opening-a-project-specific-editor"></a>打开项目特定编辑器  
 使用以下过程打开已打开的文件的特定于项目的编辑器。  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>若要打开打开的文件的项目特定编辑器  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法。  
  
     如果适当，此调用返回到文档的层次结构、 层次结构项和窗口框架指针。  
  
2.  如果文档处于打开状态，必须检查该项目以查看是否存在只属于文档数据对象，或文档视图对象是否也存在。  
  
    -   如果文档视图对象存在，并且此视图是不同的层次结构或层次结构项，project 将使用指向该视图的窗口框架的指针来 resurface 现有窗口。  
  
    -   如果文档视图对象存在，并且此视图的同一层次结构和层次结构项，项目可打开第二个视图，如果它可以将附加到基础文档数据对象。 否则，该项目应使用指向该视图的窗口框架的指针以 resurface 现有窗口。  
  
    -   如果仅存在文档数据对象，该项目应确定它是否可以为其视图使用文档数据对象。 如果兼容的文档数据对象，完成步骤中所述[打开项目特定编辑器](../extensibility/how-to-open-project-specific-editors.md)。  
  
     如果文档数据对象不兼容，错误应显示给用户，该值指示该文件当前正在使用中。 此错误应仅显示在暂时性的情况下，如文件在同一时间在编译时用户尝试通过以外使用编辑器中打开文件[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文本编辑器。 核心文本编辑器可以与编译器共享文档数据对象。  
  
3.  如果文档未打开，因为没有文档数据对象或文档视图对象，请完成中的步骤[打开项目特定编辑器](../extensibility/how-to-open-project-specific-editors.md)。  
  
## <a name="opening-a-standard-editor"></a>打开标准编辑器  
 使用以下过程来打开已的文件的标准编辑器打开。  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>若要打开打开的文件的标准编辑器  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
     此方法首先验证，该文档不是已打开通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>。 如果文档已打开，然后重新呈现其编辑器窗口。  
  
2.  如果文档未打开，然后完成中的步骤[如何： 打开标准编辑器](../extensibility/how-to-open-standard-editors.md)。  
  
## <a name="see-also"></a>另请参阅  
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 打开项目特定编辑器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何：打开标准编辑器](../extensibility/how-to-open-standard-editors.md)