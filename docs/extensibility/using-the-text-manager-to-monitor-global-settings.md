---
title: "使用文本管理器来监视全局设置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的监视全局设置"
  - "编辑器 [Visual Studio SDK]，旧的文本管理器"
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 使用文本管理器来监视全局设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果实现一个核心编辑器，您必须监视对全局设置的更改，，因为这些更改会影响编辑器的实例。  可以通过侦听跟踪更改文本管理器引发的事件。  例如，那么，当您为元素的外观或行为指定全局首选项在核心编辑器\) 时，其文档数据对象，文本管理器将此信息存储和传达它使所有受影响的客户端。  
  
## 文本管理器功能  
 文本管理器引发许多事件设置事件，包括:  
  
-   缓冲区是否在源代码管理下  
  
-   如何文件更改通知的注册  
  
-   如何跟踪哪些视图与某些缓冲区  
  
-   文本着色首选项  
  
-   选项与空间首选项  
  
 对特定语言是唯一的首选项不受文本管理器管理。  必须由每种语言服务管理这些设置。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> 接口提供文本管理器的事件通知。  实现在处理事件的对象所引发文本管理器的客户端此接口。  您这些事件注册通过在文本管理器的 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 接口。  
  
## 请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [Editor Features](http://msdn.microsoft.com/zh-cn/bdac940d-1f14-4019-a01f-fd0bb3dc7198)