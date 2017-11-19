---
title: "添加项目和项目项模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0201d2f282365a028b6251324b07276c995621ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-project-and-project-item-templates"></a>添加项目和项目项模板
在创建您自己的项目类型时，你必须使用标准将添加新项目和项目项提供支持[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成开发环境 (IDE) 对话框。 以下主题讨论不同的技术来添加项目和项目项。  
  
## <a name="in-this-section"></a>本节内容  
 [项目上下文](../../extensibility/internals/project-context.md)  
 介绍该项目提供了大部分什么调查在环境中的上下文信息。  
  
 [项目优先级](../../extensibility/internals/project-priority.md)  
 说明的项目项通常是个项目的成员，以帮助避免的多义性哪些项目用于打开该项目。  
  
 [杂项文件项目](../../extensibility/internals/miscellaneous-files-project.md)  
 提供有关可用来打开文件的项目和角色的编辑器的两种类型的信息在确定使用打开的项目项时的编辑器中扮演的项目。  
  
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)  
 说明所发生的情况时[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]创建项目。  
  
 [将项添加到“添加新项”对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 说明将项添加到的过程**添加新项**对话框。  
  
 [将目录添加到“新建项目”对话框](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 提供注册包含由 VSPackage 提供的自定义模板的新目录的一个示例。  
  
 [将目录添加到“添加新项”对话框](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 提供了注册一组新的目录的一个示例**添加新项**对话框。  
  
 [用于扩展项目系统的 IDE 定义的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 列出不同类型的命令项用于扩展项目系统。  
  
 [通常用于扩展项目的对象的 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 列出用于扩展的对象的 Catid [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]项目系统。  
  
## <a name="related-sections"></a>相关章节  
 [如何：打开项目特定的编辑器](../../extensibility/how-to-open-project-specific-editors.md)  
 提供有关打开本质上绑定到特定编辑器项目的项的分步说明。  
  
 [如何：打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)  
 提供用于打开标准编辑器的分步说明。  
  
 [项目子类型](../../extensibility/internals/project-subtypes.md)  
 提供指向项目子类型概念性主题的链接。 项目子类型扩展现有[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]项目。  
  
 [项目类型](../../extensibility/internals/project-types.md)  
 提供的其他主题提供有关如何设计新的项目类型的信息的链接。