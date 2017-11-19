---
title: "自动化模型概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d4fda81b18824560276c1398583b2674bf200ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="automation-model-overview"></a>自动化模型概述
自动化模型包含一组可以对其编写的 Visual Studio 外接程序或扩展的对象。 外接程序是应用程序可以操作在 Visual Studio 环境并自动执行常见任务。 Visual Studio 扩展可以创建自定义 Visual Studio 组件，或将添加到标准组件 （如文本编辑器） 的功能。  
  
## <a name="objects-in-the-automation-model"></a>自动化模型中的对象  
 自动化模型由相关组的对象用于控制常见环境的主要方面组成。 下面是显示了一组广泛的撰写自动化模型的对象的关系图。  
  
 ![Visual Studio 自动化对象图](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio 自动化对象  
  
 有关详细信息，请参阅[扩展 Visual Studio 环境](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。  
  
 环境的不同功能区域提供的模型。 例如，没有代码可能会发现你的各个元素的代码模型。 没有为各种文档元素的文档模型。 一个区域中，项目区域中，是 VSPackage 提供程序特定感兴趣。 你将很可能需要新的项目类型作为基本相同的方法中促成自动化模型[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]参与自动化模型。 过程所示[为 Vspackage 提供 Automation](../../extensibility/internals/providing-automation-for-vspackages.md)。  
  
 你可以考虑扩展自动化模型的环境的位置：  
  
-   Project  
  
-   Document  
  
-   代码  
  
-   生成  
  
 有关自动化的详细信息，请参阅[Visual Studio 的自动化和扩展性](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6)。 本文档和文档所提供的链接可，帮助你做出关于如何应提供为你的 VSPackage 的自动化的决策。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建外接程序](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)