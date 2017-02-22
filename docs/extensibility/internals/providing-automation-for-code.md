---
title: "提供代码的自动化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeModel 对象"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 提供代码的自动化
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

代码的一个自动化模型不需要创建。  环境 SDK 为这样做不提供一个示例。  有关深入了解代码模型中，请参见 <xref:EnvDTE.CodeModel> 对象。  
  
 若要实现代码模型，则必须实现内部数据结构依赖的所有接口。  必须从 `IDispatch`类派生对象。  
  
 您将扩展对象， <xref:EnvDTE.CodeModel> 和 <xref:EnvDTE.FileCodeModel>，从 <xref:EnvDTE.Project> 对象中可用，并且类似于:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 您可以决定实现 `CodeModel` 或 `FileCodeModel` 接口在从 `Project` 和 <xref:EnvDTE.ProjectItem> 对象返回的对象。  提供了用于项目系统适用于此接口的所有功能。  
  
 如果要添加功能，如方法或属性，从标准 `CodeModel` 和 `FileCodeModel` 接口不可用，请创建拥有从该标准继承的接口。  确保文档它与项目系统，因此最终用户知道查找它。  您返回标准接口，但是，用户可以调用 `QueryInterface` 方法或强制转换为接口，如果已知存在。  
  
## 请参阅  
 [自动化模型概述](../../extensibility/internals/automation-model-overview.md)