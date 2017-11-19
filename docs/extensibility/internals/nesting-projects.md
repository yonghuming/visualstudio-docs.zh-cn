---
title: "嵌套项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4207903fdd0f9a1462460d7f7cb2704e70e08df6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="nesting-projects"></a>嵌套项目
企业应用程序开发人员使用 VS 包可以方便地进行分组相似类型的项目中合并在一起[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用*项目嵌套*。 例如，企业级模板项目到类别中使用嵌套的项目与组项目。 商业外观项目、 Web UI 项目，依次类推组合在一起一个类别中。  
  
 在此方案中，的项目开发人员可以嵌套在每个父项目，下面的数量没有限制尽管开发人员可以以编程方式提供限制。 这种类型的分组还可递归的在这种情况下为子项目的相同类型的项目可以嵌套在子成为子项目的父级的子级的子项目。  
  
 项目嵌套不内部属于[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 你必须编写代码以启用嵌套和子项目子项目中的嵌套。 父项目是一个特殊的 VSPackage 或项目类型，创建并注册其自己的 GUID，其中包含实现项目嵌套所需的代码。  
  
 你可以在 C# Example.Nested 项目示例找到嵌套项目的示例。  
  
## <a name="nested-projects-example"></a>嵌套的项目示例  
 ![嵌套项目解决方案](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
嵌套的项目示例  
  
## <a name="see-also"></a>另请参阅  
 [如何： 实现嵌套的项目](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [卸载和重新加载嵌套项目时的注意事项](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [嵌套的项目的向导支持](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [实现处理嵌套的项目的命令](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [筛选嵌套项目 AddItem 对话框](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [上下文参数](../../extensibility/internals/context-parameters.md)   
 [向导 (.Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)