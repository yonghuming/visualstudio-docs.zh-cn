---
title: "如何： 实现错误标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d926a498549e868e478d83b7930f5e569f49ce20
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-error-markers"></a>如何： 实现错误标记
错误标记 （或红色的波浪形下划线） 是最困难的文本编辑器自定义项，来实现的。 但是，它们提供给你的 VSPackage 的用户的好处可以远远超过，让他们的成本。 错误标记稍标记语言分析器认为正确带有波浪或波浪红色下划线的文本。 此指标的帮助程序员直观地显示不正确的代码。  
  
 使用文本标记来实现红色的波浪形下划线。 一般来说，语言服务将添加红色的波浪形下划线到文本缓冲区作为后台阶段中，在空闲时或在后台线程中。  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>若要实现红色的波浪下划线功能  
  
1.  选择要在其下放置红色的波浪下划线的文本。  
  
2.  创建类型的标记`MARKER_CODESENSE_ERROR`。 有关详细信息，请参阅[如何： 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)。  
  
3.  之后，传入<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>接口指针。  
  
 此过程还允许你通过给定的标记创建提示文本或特殊的上下文菜单。 有关详细信息，请参阅[如何： 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)。  
  
 在显示错误标记之前，以下对象是必需的。  
  
-   分析器。  
  
-   任务提供程序 (即的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>)，以便确定要重新分析中的行中维护的行信息中的更改记录。  
  
-   捕获插入符号的文本视图筛选器更改事件视图使用从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) 方法。  
  
 分析器、 任务提供程序和筛选器提供使错误标记可能所需的基础结构。 以下步骤提供了用于显示错误标记的进程。  
  
1.  在要筛选视图，筛选器包含一个指向该视图的数据与关联的任务提供程序。  
  
    > [!NOTE]
    >  为方法提示、 语句完成、 错误标记和等等，可以使用相同的命令筛选器。  
  
2.  当筛选器收到一个事件以指示你已移至另一个行时，将创建任务，以检查有错误。  
  
3.  任务处理程序检查行是否已更新。 如果是这样，它将分析错误的行。  
  
4.  如果发现错误，任务提供程序将创建一个任务项实例。 此实例创建该环境使用作为文本视图中的错误标记的文本标记。  
  
## <a name="see-also"></a>另请参阅  
 [使用文本标记用于旧 API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)   
 [如何： 使用文本标记](../extensibility/how-to-use-text-markers.md)