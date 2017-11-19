---
title: "Visual Studio 中的层次结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a651267ed279fa5efaf14efb4f1f866794c5cc3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio 中的层次结构
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 显示为项目*层次结构*。 在 IDE 中，层次结构是的节点，其中每个节点具有一组关联的属性的树。 A*项目层次结构*是保存项目的项、 的项的关系和项目的关联的属性和命令的容器。  
  
 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，通过使用层次结构界面、 管理项目层次结构<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口将重定向到相应的层次结构窗口而不是标准命令处理程序调用从项目项的命令。  
  
## <a name="project-hierarchies"></a>项目层次结构  
 每个项目层次结构包含你可以查看和编辑的项。 这些项会因项目类型的不同而异。 例如，一个数据库项目可能包含存储的过程、 数据库视图和数据库表。 另一方面，编程语言的项目中，将可能包括源文件和位图和对话框框中的资源文件。 可以嵌套层次结构，后者提供一些更大的灵活性时创建的项目层次结构。  
  
 当你创建新的项目类型时，该项目类型控制可以在其中编辑的项的完整集合。 但是，项目可以包含为其无权编辑支持的项。 例如，Visual c + + 项目可以包含 HTML 文件，即使 Visual c + + 中不提供为 HTML 文件类型的任何自定义的编辑器。  
  
 层次结构管理它们所包含的项的持久性。 层次结构的实现必须控制会影响层次结构中的项的持久性任何特殊属性。 例如，如果项表示而不是文件的存储库中的对象，层次结构实现必须控制这些对象的持久性。 IDE 本身指示要保存符合用户输入的项的层次结构，但 IDE 不控制保存这些项所需的任何操作。 相反，项目是在控件中。  
  
 当用户在编辑器中打开某个项时，控制该项目的层次结构选择，并且将成为活动的层次结构。 所选层次结构确定的一套命令可用于在项上执行操作。 跟踪用户焦点以这种方式使层次结构，以反映用户的当前上下文。  
  
## <a name="see-also"></a>另请参阅  
 [项目类型](../../extensibility/internals/project-types.md)   
 [选择和 IDE 中的货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [VSSDK 示例](http://aka.ms/vs2015sdksamples)