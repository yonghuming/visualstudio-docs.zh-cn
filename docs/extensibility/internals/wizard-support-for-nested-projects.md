---
title: "嵌套项目的向导支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "添加项目向导"
  - "嵌套的项目中，向导支持"
  - "新建项目向导"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 嵌套项目的向导支持
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE 运行嵌套项的父级项目能够实现的两个向导: **新项目** 向导和 **添加项目** 向导。  
  
 如果用户启动 **新项目** 向导通过选择 **添加项目** 然后单击 **新项目** 在 " 文件 " 菜单或通过选择 **添加** 和右击在解决方案资源管理器中 **新项目** ， IDE 运行 **AddProject** 命令，并 **AddProject** 命令的父项目实现返回模板项目文件或设置上下文参数的向导 \(.vsz\) 文件。  
  
 同样， **AddItem** 向导的父项目实现返回具有不同设置上下文参数的 .vsz 文件。  
  
 有关向导的更多信息，请参见 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)、 [上下文参数](../../extensibility/internals/context-parameters.md) 和 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)