---
title: "在编辑器中的旧接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4b437dad35850a20696702b84d8ea98ead8a1e9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-interfaces-in-the-editor"></a>在编辑器中的旧接口
你可以从旧接口访问 Visual Studio 编辑器。 Visual Studio SDK 包括适配器称为*填充码*，它实现这些接口，以便与新的编辑器进行交互。 不过，我们建议你更新旧代码以使用新的编辑器 API。 你的代码将更好地执行，你可以使用 Windows Presentation Foundation (WPF) 和 Managed Extensibility Framework (MEF) 等新技术。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[调整到编辑器的旧代码](../extensibility/adapting-legacy-code-to-the-editor.md)|说明如何调整到新的编辑器代码。|  
|[使用编辑器适配器的新的或更改行为](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|说明如何编辑器适配器的行为不同于早期版本的编辑器。|  
|[在核心编辑器](../extensibility/inside-the-core-editor.md)|介绍编辑器的早期版本的不同组件。|  
|[使用旧版 API 实例化核心编辑器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|说明如何使用旧的 API 来实例化核心编辑器。|  
|[编辑器工厂](../extensibility/editor-factories.md)|说明如何使用旧 API 编辑器工厂。|  
|[如何： 注册编辑器文件类型](../extensibility/how-to-register-editor-file-types.md)|说明如何将文件扩展名为链接到你的编辑器。|  
|[演练： 创建核心编辑器和注册编辑器文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|说明如何创建编辑器的核心并链接到它的文件扩展名。|  
|[如何： 为编辑器提供的上下文](../extensibility/how-to-provide-context-for-editors.md)|说明如何为你的编辑器提供的上下文。|  
|[语言服务和核心编辑器](../extensibility/language-services-and-the-core-editor.md)|说明语言服务和编辑器之间的交互。|  
|[通过使用旧版 API 访问文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|说明如何使用旧的 API 来访问文本缓冲区。|  
|[通过使用旧版 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|说明如何通过使用旧的 API 访问文本视图。|  
|[通过使用旧版 API 的自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|说明如何使用旧的 API 自定义代码窗口。|  
|[通过使用旧版 API 访问文本层](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|说明如何使用旧的 API 来访问的文本的不同层。|  
|[使用文本标记用于旧 API](../extensibility/using-text-markers-with-the-legacy-api.md)|说明如何使用旧的 API 添加文本标记。|  
|[使用旧版 API 自定义编辑器控件和菜单](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|说明如何使用旧的 API 自定义编辑器控件。|  
|[管理撤消和重做通过旧版 API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|说明如何管理撤消和重做通过使用旧的 API。|  
|[如何： 实现查找和替换机制](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|说明如何管理查找和替换使用旧的 API。|  
|[如何： 禁止显示文件更改通知](../extensibility/how-to-suppress-file-change-notifications.md)|说明如何使用旧 API 禁止显示文件更改通知。|  
|[创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md)|说明如何创建自定义编辑器和设计器。|  
|[开发旧版语言服务](../extensibility/internals/developing-a-legacy-language-service.md)|提供指向有关提供了对自定义功能的功能文档链接[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]通过添加对语言服务支持的核心编辑器。|  
|[使用字体和颜色](../extensibility/using-fonts-and-colors.md)|说明如何使用旧的接口的字体和颜色。|