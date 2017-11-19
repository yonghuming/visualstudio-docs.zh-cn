---
title: "杂项文件项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 514eb7a80b5e23997abb64c513af1b278bf90704
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="miscellaneous-files-project"></a>杂项文件项目
当用户打开项目项时，IDE 将分配给杂项文件项目不是解决方案中的任何项目的成员的任何项。  
  
 项目起重要作用中确定用户打开的项目项时，将使用的编辑器。 一个项目可以用于通过使用特定于项目的编辑器或标准编辑器打开某些文件。  
  
 项目特定编辑器通常要求用户具有特殊的知识，或使用从项目的特殊接口。 有关详细信息，请参阅[如何： 打开项目特定编辑器](../../extensibility/how-to-open-project-specific-editors.md)。  
  
 标准编辑器可以打开任何项目中的一个特定的扩展的任何文件。 用户可以自定义某些标准编辑器中，如[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文本编辑器中的，对于项目，但仍保留了其公共字符。 通过使用创建标准编辑器<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。  
  
 如果解决方案中的没有项目响应它可以打开的项目项，IDE 提供了一个名为打开任何文件的杂项文件项目的特殊项目。  
  
 此特殊项目提供了用于打开的文件在项目上下文之外。 处理过程中<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>杂项文件项目的方法，始终响应具有非常低的优先级。 因此，杂项文件始终投影到任何可打开文件的优先级较高的项目的生成。  
  
 杂项文件项目不需要用户显式创建它与**新项目**对话框。 此外，杂项文件项目不永久管理项目成员的列表。 它使用一项可选功能来记录每个用户最近使用过的文件的列表。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [如何： 打开项目特定编辑器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何： 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)