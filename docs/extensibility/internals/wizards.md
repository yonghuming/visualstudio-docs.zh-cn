---
title: "向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 838b7cac850b8e7eb3401065cf13202d3a3a40ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="wizards"></a>向导
创建向导后，你通常想要将其添加到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成开发环境 (IDE)，以便其他人可以用它。 添加的向导则出现在**添加新项目**或**添加新项**对话框。 若要查看**添加新项目**或**添加新项**对话框框中，右键单击打开的解决方案中**解决方案资源管理器**，指向**添加**，和然后单击**新项目**或**新项**。  
  
 在可实现向导[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以使用户可以从可用的值，当用户打开时的树视图中选择**添加新项目**对话框中或**添加新项**对话框中，或当它们右键单击中的项**解决方案资源管理器**。  
  
 在向导中，你可以提供的本地化名称的新项目或 ites，选项，你可以确定当用户选择该向导时，用户将看到的图标。 你还可以控制新的项相对于其他可用的项; 出现的顺序项不需要按字母顺序组织。  
  
 你也可以提供一个向导，以不同方式，启动基于打开时将它传递给向导的自定义参数。  
  
 本部分中的主题讨论的文件，实现它可导致[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**添加新项目**和**添加新项**对话框中，若要列出可用的向导和模板之间的向导和向导在 IDE 中正确运行所必须满足的要求。  
  
## <a name="in-this-section"></a>本节内容  
 [模板目录说明 (.Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 提供的模板概述 directory 说明文件并说明如何显示文件夹、 向导.vsz 文件和与在对话框中的项目相关联的模板文件在 IDE 中的工作方式。  
  
 [向导 (.Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)  
 解释如何在 IDE 启动向导，并列出.vsz 文件的三个部分。  
  
 [向导界面 (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 描述`IDTWizard`向导为在 IDE 中工作而必须实现的接口。  
  
 [上下文参数](../../extensibility/internals/context-parameters.md)  
 说明如何实现向导以及 IDE 将上下文参数传递给实现时，所发生的情况。  
  
 [自定义参数](../../extensibility/internals/custom-parameters.md)  
 说明如何使用自定义参数来控制的操作的向导后启动向导。  
  
## <a name="related-sections"></a>相关章节  
 [项目类型](../../extensibility/internals/project-types.md)  
 提供的其他主题提供有关如何设计新的项目类型的信息的链接。  
  
 [演练： 创建向导](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 演示如何以创建向导。  
  
 [扩展项目](../../extensibility/extending-projects.md)  
 介绍如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目和解决方案来组织代码文件和资源文件，以及如何实现源代码管理。