---
title: "在编辑器中的旧式界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e6f4c118ac9306bc533ba7cf62037a8255e9c42f
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-interfaces-in-the-editor"></a>在编辑器中的旧接口
您可以从旧式界面访问 Visual Studio 编辑器中。 Visual Studio SDK 包括适配器称为*填充码*，它实现了这些接口，以便与新编辑器进行交互。 不过，我们建议您更新旧代码以使用新的编辑器 API。 您的代码将更好地执行，可以使用 Windows Presentation Foundation (WPF) 和 Managed Extensibility Framework (MEF) 等新技术。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|说明|  
|-----------|-----------------|  
|[调整到编辑器的旧代码](../extensibility/adapting-legacy-code-to-the-editor.md)|说明如何以适应你的代码与新的编辑器。|  
|[新的或更改行为与编辑器适配器](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|说明如何编辑器适配器的行为不同于早期版本的编辑器。|  
|[在核心编辑器](../extensibility/inside-the-core-editor.md)|介绍编辑器的早期版本的不同组件。|  
|[实例化使用旧 API 的核心编辑器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|说明如何使用传统的 API 来实例化核心编辑器。|  
|[编辑器工厂](../extensibility/editor-factories.md)|说明如何使用传统的 API 的编辑器工厂。|  
|[如何︰ 注册编辑器文件类型](../extensibility/how-to-register-editor-file-types.md)|说明如何将文件扩展名为链接到您的编辑器。|  
|[演练︰ 创建核心编辑器和注册了编辑器中的文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|说明如何创建编辑器的一个核心，并将文件扩展名为链接到它。|  
|[如何︰ 为编辑器提供的上下文](../extensibility/how-to-provide-context-for-editors.md)|说明如何为您的编辑器提供的上下文。|  
|[语言服务和核心编辑器](../extensibility/language-services-and-the-core-editor.md)|解释语言服务和一个编辑器之间的交互。|  
|[通过使用旧 API 访问文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|说明如何通过使用传统的 API 访问文本缓冲区。|  
|[通过使用旧 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|说明如何通过使用传统的 API 访问文本视图。|  
|[通过使用旧 API 的自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|说明如何通过使用传统的 API 自定义代码窗口。|  
|[通过使用旧 API 的访问将文本层](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|说明如何通过使用传统的 API 访问的文本的不同层。|  
|[使用旧 API 使用文本标记](../extensibility/using-text-markers-with-the-legacy-api.md)|说明如何通过使用传统的 API 添加文本标记。|  
|[通过使用旧 API 自定义编辑器控件和菜单](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|说明如何通过使用传统的 API 自定义编辑器控件。|  
|[管理撤消和重做通过使用旧 API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|说明如何管理撤消和重做通过传统的 API。|  
|[如何︰ 实现查找和替换机制](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|说明如何管理查找和替换使用传统的 API。|  
|[如何︰ 禁止显示文件更改通知](../extensibility/how-to-suppress-file-change-notifications.md)|说明如何通过使用传统的 API 来禁止显示文件更改通知。|  
|[创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md)|说明如何创建自定义编辑器和设计器。|  
|[开发旧语言服务](../extensibility/internals/developing-a-legacy-language-service.md)|提供指向有关提供了对自定义功能的功能文档链接[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器，通过添加对语言服务的支持。|  
|[使用字体和颜色](../extensibility/using-fonts-and-colors.md)|说明如何使用旧接口使用的字体和颜色。|
