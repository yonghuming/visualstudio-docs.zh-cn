---
title: "项目优先级 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51ed8cd351a306c3992b4b6c9fcc2231a90085f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-priority"></a>项目优先级
项目项通常是解决方案中只有一个项目的成员。 因此，IDE 可以轻松地确定哪些项目用于打开该项目。 但是，如果项是多个项目的成员，IDE 将使用优先级方案来确定打开项的最佳项目。  
  
 以下列表显示的项目优先级方案：  
  
-   IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>要确定文档是否为该项目的成员的解决方案中每个项目的方法。  
  
-   如果文档是项目的成员，项目响应优先级项目分配根据其处理该文档。 例如，语言项目将使用其语言源文件的高优先级进行响应，但将使用较低的优先级不用作其生成过程的一部分的无法识别的文件类型进行响应。  
  
-   文档中提供自定义、 项目特定的编辑器或设计器的项目还会收到高优先级。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>枚举提供文档优先级值。  
  
-   指定的最高优先级项目有打开的文档的上下文。 如果两个项目返回相同的优先级值，将首选活动项目。 如果解决方案中的没有项目响应，它可以打开的文档，IDE 会将文档置于杂项文件项目。 有关详细信息，请参阅[杂项文件项目](../../extensibility/internals/miscellaneous-files-project.md)。  
  
## <a name="see-also"></a>另请参阅  
 [杂项文件项目](../../extensibility/internals/miscellaneous-files-project.md)   
 [如何： 打开编辑器的打开的文档](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)