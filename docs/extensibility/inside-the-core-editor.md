---
title: "核心编辑器内 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50db39e9a6b864df8876054b455b169531260a9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="inside-the-core-editor"></a>在核心编辑器
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器是一套可使你修改和查询文本信息的多个组件。 如果通过使用旧 API 定义了核心编辑器，可继续使用这些自定义，将通过编辑器适配器路由。 建议，但是，你调整到新的编辑器 API 你自定义项。  
  
 以下几个方面是核心编辑器一些重要方面：  
  
-   文本缓冲区  
  
-   文本视图  
  
-   “代码”窗口  
  
-   文本标记  
  
-   文本管理器  
  
-   与语言服务的集成  
  
## <a name="in-this-section"></a>本节内容  
 [使用旧版 API 实例化核心编辑器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 提供有关如何使用的分步说明<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>编辑器创建核心的实例。  
  
 [通过使用旧版 API 访问文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 讨论核心编辑器中的文本缓冲区的角色，说明用于访问缓冲区，并提供由文本缓冲区对象实现的接口的列表的关联的系统<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 [旧版 API 中的文本缓冲区事件](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 提供的接口的用于通知的文本缓冲区事件列表。  
  
 [如何： 为与旧版 API 的文本缓冲区事件注册](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 描述如何告知文本缓冲区事件。  
  
 [使用文本管理器来监视全局设置](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 讨论如何使用文本管理器以与核心编辑器组件共享全局首选项信息以及如何接收的文本管理器事件通知。  
  
 [通过使用旧版 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 描述在核心编辑器中的文本视图的角色，并列出由实现的接口<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>对象。  
  
 [通过使用旧版 API 的自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 提供有关代码窗口用于括起的文本视图、 讨论如何使用代码窗口管理器来提供到代码窗口中，修饰和提供的新视图的通知的信息。  
  
 [通过使用旧版 API 更改视图设置](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 提供有关如何强制视图设置以及如何删除强制的设置的分步说明。  
  
 [语言服务和核心编辑器](../extensibility/language-services-and-the-core-editor.md)  
 描述某种语言服务的控制代码修饰实例化。  
  
## <a name="related-sections"></a>相关章节  
 [演练： 创建核心编辑器和注册编辑器文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 提供有关如何从托管代码中启动核心编辑器的分步说明。  
  
 [下拉栏](../extensibility/drop-down-bar.md)  
 讨论如何下拉栏代码窗口中使用，并描述实现下拉栏时使用的接口。  
  
 [使用文本标记用于旧 API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 说明文本标记以及如何在核心编辑器中，使用它们的概念，并列出用于访问和管理文本标记的接口。  
  
 [如何： 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)  
 提供有关如何创建一个文本标记以及如何将自定义命令添加到快捷菜单的分步说明。  
  
 [如何： 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)  
 提供有关如何创建自定义文本标记以及如何提供标记类型作为服务的分步说明。