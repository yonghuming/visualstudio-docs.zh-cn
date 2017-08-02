---
title: "自动化模型概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 12
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
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>自动化模型概述
自动化模型包含一组可以对其编写的 Visual Studio 外接程序或扩展的对象。 外接程序是可以处理 Visual Studio 环境并自动执行常见任务的应用程序。 Visual Studio 扩展可以创建自定义 Visual Studio 组件，或将添加到标准组件，例如文本编辑器的功能。  
  
## <a name="objects-in-the-automation-model"></a>自动化模型中的对象  
 自动化模型由相关组的对象，用于控制常见环境的主要方面。 下面是显示一组广泛的对象编写自动化模型的关系图。  
  
 ![Visual Studio 自动化对象图](~/docs/extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio 自动化对象  
  
 有关详细信息，请参阅[扩展 Visual Studio 环境](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。  
  
 环境的不同功能区域提供的模型。 例如，是您可能会发现在代码中的各种元素受代码模型。 没有文档模型的各种文档元素。 一个区域中，项目区域中，是对 VSPackage 提供程序特定的感兴趣。 您可能希望将新的项目类型参与到自动化模型中更像那样[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]有利于实现自动化模型。 过程所示[VSPackages 提供自动化](../../extensibility/internals/providing-automation-for-vspackages.md)。  
  
 您可以考虑扩展的环境的自动化模型的位置︰  
  
-   Project  
  
-   Document  
  
-   代码  
  
-   生成  
  
 有关自动化的详细信息，请参阅[的 Visual Studio 自动化和扩展性](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6)。 本文档和文档它提供链接，帮助您做出决定，您应如何提供你的 VSPackage 的自动化。  
  
## <a name="see-also"></a>另请参阅  
 [如何︰ 创建外接程序](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
