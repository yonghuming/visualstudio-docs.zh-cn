---
title: "项目上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
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
ms.openlocfilehash: d74d804f65338edb589e63dde111e2ec1a4b5c6f
ms.lasthandoff: 02/22/2017

---
# <a name="project-context"></a>项目上下文
当用户将添加或适用于项目和项目项时，IDE 将使用项目上下文的概念来确定应执行各种操作。  
  
 通常情况下，文件是用户通过选择来显式创建的标准项目对象**新项目**命令或可通过选择用于**打开项目**命令**文件**菜单。 在这些情况下，创建和项目的上下文中打开文件和项目类型定义编辑文档的上下文。  
  
 某些项目提供非常丰富的上下文。 例如，项目管理项目范围、 编程的命名空间或进行数据绑定的项目范围的数据库连接。 用户可以经常打开的文件或数据库连接直接通过使用一个特定项目对象，如在解决方案资源管理器中显示的项目项。  
  
 在其他时候，项目的项目上下文未显式指定。 例如，某一项的上下文不可用时用户选择打开的文件**打开现有文件**命令**文件**菜单、 何时调试器都将运行文件，或当用户单击**在文件中查找**命令**查找和替换**对话框。 若要处理这些情况下，IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>管理查找最佳的项目以打开的文档的过程。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>  
  
## <a name="see-also"></a>另请参阅  
 [项目优先级](../../extensibility/internals/project-priority.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)
