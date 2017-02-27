---
title: "如何: 实现错误标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的错误的标记"
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何: 实现错误标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

错误标记 \(或红色波浪下划线\) 是最难文本编辑器自定义实现。  但是，它们以生成 VSPackage 用户的优势会超过成本提供。  错误标记细微文本标记语言分析器视为错误到曲线编写或红色波浪线。  此指示符通过直观地显示不正确的编码帮助程序员。  
  
 使用文本标记实现红色波浪下划线。  通常，语言服务添加红色波浪下划线到文本缓冲区作为背景通过，在空闲时间或在后台线程。  
  
### 实现红色波浪下划线功能  
  
1.  选择下要让红色波浪下划线的文本。  
  
2.  创建类型 `MARKER_CODESENSE_ERROR`的标记。  有关更多信息，请参见 [如何: 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)。  
  
3.  在此之后，请通过在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口指针。  
  
 此过程还允许您创建提示文本或特定上下文菜单在特定标记。  有关更多信息，请参见 [如何: 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)。  
  
 下面的对象，在错误标记，然后才能显示需要。  
  
-   一个分析器。  
  
-   保持更改记录在行信息中的来标识是重新分析的行的任务提供程序 \(即实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>\)。  
  
-   使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>\) 方法，从视图获取插入符号更改事件的文本视图筛选器。  
  
 分析器、任务提供程序和筛选器提供必要的基础结构使错误标记成为可能。  以下步骤为显示错误标记提供处理。  
  
1.  在筛选的视图，筛选器获取指向任务提供程序与该视图中的数据。  
  
    > [!NOTE]
    >  可以为方法提示使用同一个命令筛选器，语句完成，错误标记，依此类推。  
  
2.  在筛选器接收清单时的事件已移动到另一行，创建任务时检查错误。  
  
3.  任务处理程序检查行是否已更新。  如果是，则分析错误的行。  
  
4.  如果发现错误，任务提供程序创建任务项实例。  此实例创建环境用作错误标记在文本视图的文本标记。  
  
## 请参阅  
 [使用旧 API 使用文本标记](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何: 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)   
 [如何: 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)   
 [如何: 使用文本标记](../extensibility/how-to-use-text-markers.md)