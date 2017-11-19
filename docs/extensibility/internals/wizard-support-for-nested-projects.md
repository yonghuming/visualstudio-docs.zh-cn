---
title: "嵌套的项目的向导支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7191d31d4ec53fb26f4ab20114201836f1b58fc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-support-for-nested-projects"></a>嵌套的项目的向导支持
IDE 运行嵌套项目的父项目可以实现的两个向导：**新项目**向导和**添加项**向导。  
  
 如果用户启动**新项目**向导通过选择**添加项目**并单击**新项目**文件菜单上或通过选择**添加**右键单击**新项目**在解决方案资源管理器，IDE 将运行**AddProject**命令和父项目实现**AddProject**命令返回模板项目文件中或具有一组上下文参数的向导 (.vsz) 文件。  
  
 同样，父项目的实现**AddItem**向导返回具有一组不同的上下文参数的.vsz 文件。  
  
 有关向导的详细信息，请参阅[向导 (。Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)，[上下文参数](../../extensibility/internals/context-parameters.md)和[注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)