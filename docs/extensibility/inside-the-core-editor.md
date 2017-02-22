---
title: "在核心编辑器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的核心编辑器"
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 在核心编辑器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心编辑器是允许您修改和查询文本信息的设置多个元素。  使用传统的 API，如果自定义核心编辑器，您可以继续使用这些自定义，通过编辑适配器将路由。  建议使用，但是，改编自定义项的新编辑器 API。  
  
 以下区域是核心编辑器的一些重要方面:  
  
-   文本缓冲区  
  
-   文本视图  
  
-   代码窗口  
  
-   文本标记  
  
-   文本管理器  
  
-   与语言服务的集成  
  
## 本节内容  
 [实例化使用旧 API 的核心编辑器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 提供有关如何的分步说明使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 创建核心编辑器的实例。  
  
 [通过使用旧 API 访问文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 讨论在核心编辑器中的文本缓冲区的角色，解释用于访问缓冲区关联的系统，并提供文本缓冲区对象实现的接口的列表， <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 [旧 API 中的文本缓冲区事件](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 提供文本缓冲区事件通知使用接口的列表。  
  
 [如何: 为与旧 API 的文本缓冲区事件注册](../Topic/How%20to:%20Register%20for%20Text%20Buffer%20Events%20with%20the%20Legacy%20API.md)  
 描述如何建议文本缓冲区事件。  
  
 [使用文本管理器来监视全局设置](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 讨论文本管理器如何在与内核编辑元素共享全局首选项信息以及如何接收文本管理器事件的通知。  
  
 [通过使用旧 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 描述在核心编辑器中的文本视图的角色和列表 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 对象实现的接口。  
  
 [通过使用旧 API 的自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 提供有关如何代码窗口的信息用于将文本视图，讨论代码窗口管理器如何用于提供修饰到代码窗口，并提供新视图的通知。  
  
 [通过使用旧 API 更改视图设置](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 提供有关如何强制视图设置以及如何的分步说明移除强制的设置。  
  
 [语言服务和核心编辑器](../extensibility/language-services-and-the-core-editor.md)  
 描述语言服务的实例化控件代码修饰。  
  
## 相关章节  
 [演练: 创建核心编辑器和注册了编辑器中的文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 提供有关如何的分步说明开始从托管代码的核心编辑器。  
  
 [下拉栏](../extensibility/drop-down-bar.md)  
 讨论该下拉栏如何在代码窗口并描述使用的接口，在实现一个下拉栏时。  
  
 [使用旧 API 使用文本标记](../extensibility/using-text-markers-with-the-legacy-api.md)  
 解释文本标记的概念以及如何在核心编辑器，并列出用于访问和管理文本标记的接口。  
  
 [如何: 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)  
 提供有关如何创建文本标记以及如何的分步说明添加自定义命令添加到快捷菜单。  
  
 [如何: 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)  
 提供有关如何创建自定义文本标记以及如何的分步说明提供标记类型用作服务。