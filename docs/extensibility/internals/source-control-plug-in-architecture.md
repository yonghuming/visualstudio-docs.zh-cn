---
title: "源控件插件体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0cde4ca360aa0059abcbe0b64d63b4a94e85d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-architecture"></a>源控件插件体系结构
可以添加到源控件支持[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 的实现并附加了源代码管理插件。 IDE 将连接到源代码管理插件通过定义完善的源控件插件 API。 IDE 提供组成工具栏和菜单命令的用户界面 (UI) 来公开的源控制系统版本控制功能。 源代码管理插件实现源代码管理功能。  
  
## <a name="source-control-plug-in-resources"></a>源控件插件资源  
 源代码管理插件提供资源以帮助创建并连接到应用程序版本控制[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 源代码管理插件包含，以便它可以集成到源代码管理插件必须实现的 API 规范[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 它还包含实现的主干源控件插件演示实现符合源控制插件 API 的基本功能的代码示例 （c + + 编写）。  
  
 源控件插件 API 规范允许您利用所选的任何源代码管理系统，如果使用组所需的函数根据源控制插件 API 实现创建源控件 DLL。  
  
## <a name="components"></a>组件数  
 关系图中的源控件适配器包是将转换为函数调用受源代码管理插件的源控制操作的用户的请求在 IDE 的组件。 这种情况，IDE 和源代码管理插件必须具有一个有效的对话框，它 IDE 和插件之间来回传递信息。 有关此对话框中进行，它们都必须讲相同的语言。 本文档中所述的源控件插件 API 是为此 exchange 的常见词汇。  
  
 ![源代码控件体系结构关系图](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
显示 VS 和源控件之间的交互插件体系结构图示  
  
 体系结构关系图中中, 所示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell，作为 VS shell 在图中，标记为托管用户的工作项目和关联的组件，例如编辑器和解决方案资源管理器。 源代码管理适配器包处理 IDE 和源代码管理插件之间的交互。 源代码管理适配器包提供其自己的源代码管理 UI。 它是顶级以便启动并定义源代码管理操作的作用域与用户交互的 UI。  
  
 源代码管理插件可以有其自己的 UI，可能包含两个部分，如图中所示。 标记为"供应商 UI"的框表示你，作为源控件插件创建者，提供的自定义用户界面元素。 当用户调用高级的源代码管理操作，这些不显示直接通过源代码管理插件。 标有"帮助程序 UI"的框是一组的源控件可以间接通过 IDE 调用的插件 UI 功能。 源代码管理插件将 UI 相关的消息传递到通过由 IDE 提供特殊的回调函数 IDE。 帮助器 UI 便于与 IDE 更无缝集成 (通常通过使用的**高级**按钮) 并因此提供更加一致的最终用户体验。  
  
 源代码管理插件不能进行更改到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell，因此，对源控件适配器包或源控制由 IDE 提供用户界面。 它必须进行最大使用通过贡献集成体验的最终用户的各种源控件插件 API 函数的实现所提供的灵活性。 源控件插件 API 文档的参考部分包括一些高级的源代码管理插件功能的信息。 若要利用这些功能，源代码管理插件必须声明为 IDE 其高级的功能在初始化期间，和它必须实现每个功能的特定高级的函数。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件](../../extensibility/source-control-plug-ins.md)   
 [术语表](../../extensibility/source-control-plug-in-glossary.md)   
 [创建源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)