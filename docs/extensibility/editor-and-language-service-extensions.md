---
title: "编辑器和语言服务扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 67d250a2806b367a76fa593026f10d4b671c21b2
ms.lasthandoff: 02/22/2017

---
# <a name="editor-and-language-service-extensions"></a>编辑器和语言服务扩展
您可以扩展 Visual Studio 代码编辑器中的大多数功能。 编辑器基于 Windows Presentation Foundation (WPF) 上，并以托管代码编写。 尽管这种设计不同于在 Visual Studio 的早期版本中的设计，它提供的大多数相同的功能。 若要扩展编辑器，使用 Managed Extensibility Framework (MEF)。  
  
 Visual Studio SDK 提供了适配器称为*填充码*以支持 VSPackages 迁移为早期版本编写的。 不过，如果您有现有的 VSPackage，我们建议您向新的技术，以获得更好的性能和可靠性更新它。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)|介绍如何使用编辑器项模板。|  
|[扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)|链接到文档中介绍的设计和功能的核心编辑器，并演示如何对其进行扩展。|  
|[在编辑器中的旧接口](../extensibility/legacy-interfaces-in-the-editor.md)|说明如何从现有代码访问核心编辑器文档的链接。|  
|[创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md)|介绍如何创建自定义编辑器的文档链接。|  
|[遗留语言服务可扩展性](../extensibility/internals/legacy-language-service-extensibility.md)|介绍如何集成到 Visual Studio 编程语言的文档链接。|  
|[托管可扩展性框架 (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|引入了托管可扩展性框架 (MEF)。|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|引入了 Windows Presentation Foundation (WPF)。|
