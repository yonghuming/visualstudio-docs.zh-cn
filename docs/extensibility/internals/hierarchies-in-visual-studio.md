---
title: "在 Visual Studio 中的层次结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 14
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
ms.openlocfilehash: ca8fa51a14f38dcd651f26e8ed10ca48d670f37b
ms.lasthandoff: 02/22/2017

---
# <a name="hierarchies-in-visual-studio"></a>在 Visual Studio 中的层次结构
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 显示为一个项目*层次结构*。 在 IDE 中，层次结构是为节点树，其中每个节点都有一组相关联的属性。 一个*项目层次结构*是保存项目的项、 项目的关系和项目的相关的属性和命令的容器。  
  
 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，通过使用层次结构界面、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>管理项目层次结构 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口将重定向到适当的层次结构窗口而不是标准命令处理程序从项目项调用的命令。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
## <a name="project-hierarchies"></a>项目层次结构  
 每个项目层次结构包含可以查看和编辑的项。 这些项将因项目类型而异。 例如，存储的过程、 数据库视图和数据库表可能包含数据库项目。 另一方面，编程语言项目中，将可能包含源代码文件和位图和对话框的资源文件。 可以嵌套层次结构，它可以一些更大的灵活性时创建的项目层次结构。  
  
 在创建新的项目类型时，项目类型控制可以在其中编辑的项的完整集合。 但是，项目可以包含的项，它们没有编辑支持。 例如，Visual c + + 项目可以包含 HTML 文件，即使 Visual c + + 中不提供对 HTML 文件类型的任何自定义的编辑器。  
  
 层次结构管理包含的项的持久性。 层次结构的实现必须控制任何特殊属性，它们会影响层次结构中的项的持久性。 例如，如果项表示的对象而不是文件存储库中的，层次结构实现必须控制这些对象的持久性。 IDE 本身指示要保存符合用户输入的项的层次结构，但 IDE 不控制保存这些项目所需的任何操作。 相反，该项目是在控件中。  
  
 当用户在编辑器中打开某个项时，控制该项目的层次结构处于选中状态，并将成为活动的层次结构。 所选层次结构确定的一套命令，可用于对项进行操作。 跟踪用户焦点以这种方式使层次结构，以反映用户的当前上下文。  
  
## <a name="see-also"></a>另请参阅  
 [项目类型](../../extensibility/internals/project-types.md)   
 [所选内容和在 IDE 中的货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [VSSDK 示例](../../misc/vssdk-samples.md)
