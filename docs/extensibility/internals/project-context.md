---
title: "项目上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 368f6ecb67bc8b01df975da6e68e95b553a0e31d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-context"></a>项目上下文
当用户将添加或适用于项目和项目项时，IDE 将使用项目上下文的概念来确定应执行各种操作。  
  
 通常情况下，文件是通过选择来显式创建用户的标准项目对象**新项目**命令或可用于通过选择**打开项目**命令**文件**菜单。 在这些情况下，创建和打开一个项目的上下文中文件和项目类型定义编辑文档的上下文。  
  
 某些项目提供了非常丰富的上下文。 例如，项目管理项目作用域、 编程的命名空间或数据绑定的项目范围的数据库连接。 用户可以经常打开文件或数据库连接直接通过使用一个特定项目对象，如解决方案资源管理器中显示的项目项。  
  
 在其他情况下，项的项目上下文未显式指定。 例如，项的上下文时不可用的用户通过选择打开的文件**打开现有文件**命令**文件**时调试器的运行上一个文件，或当用户单击菜单**在文件中查找**命令**查找和替换**对话框。 若要处理这些情况下，在 IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>管理查找最佳的项目来打开的文档的过程。  
  
## <a name="see-also"></a>另请参阅  
 [项目优先级](../../extensibility/internals/project-priority.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)