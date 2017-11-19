---
title: "编辑器和语言服务扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e5ad07694604c7b61c922cd097809fa037e0501
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="editor-and-language-service-extensions"></a>编辑器和语言服务扩展
你可以扩展 Visual Studio 代码编辑器中的大多数功能。 编辑器是在 Windows Presentation Foundation (WPF) 和用托管代码编写。 尽管这种设计与早期版本的 Visual Studio 中设计的不同，它提供的大多数相同的功能。 若要扩展编辑器，请使用 Managed Extensibility Framework (MEF)。  
  
 Visual Studio SDK 提供了名为的适配器*填充码*以支持的早期版本编写的 Vspackage。 不过，如果你有现有的 VSPackage，我们建议，你将其更新为新的技术，以获取更好的性能和可靠性。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[使用编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)|介绍了如何使用编辑器项模板。|  
|[扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)|引入的设计和功能的核心编辑器和显示如何对其进行扩展的文档的链接。|  
|[在编辑器中的旧接口](../extensibility/legacy-interfaces-in-the-editor.md)|指向说明如何从现有代码中访问核心编辑器文档的链接。|  
|[创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md)|说明如何创建自定义编辑器的文档的链接。|  
|[旧版语言服务扩展性](../extensibility/internals/legacy-language-service-extensibility.md)|描述如何将编程语言集成到 Visual Studio 的文档的链接。|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|引入了 Managed 的 Extensibility Framework (MEF)。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|引入了 Windows Presentation Foundation (WPF)。|