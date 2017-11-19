---
title: "项目建模 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d654669ad35ce77d840f4852ceb7a6605a8221be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-modeling"></a>项目建模
你的项目实现标准项目对象提供自动化的下一步：<xref:EnvDTE.Projects>和`ProjectItems`集合;`Project`和<xref:EnvDTE.ProjectItem>对象; 和剩余的对象唯一的实现。 Dteinternal.h 文件中定义这些标准的对象。 BscPrj 示例中提供了标准的对象的实现。 可以为模型中使用这些类创建您自己独立并排显示的标准项目对象与其他项目类型的项目对象。  
  
 自动化使用者假定要能够调用<xref:EnvDTE.Solution>("`<UniqueProjName>")`和<xref:EnvDTE.ProjectItems>(`n`) 其中 n 是一个用于获取解决方案中的特定项目的索引编号。 进行此自动化调用将导致产生环境，以调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A>相应的项目层次结构，将 VSITEMID_ROOT 作为 ItemID 参数和 VSHPROPID_ExtObject 作为 VSHPROPID 参数传递。 `IVsHierarchy::GetProperty`返回`IDispatch`提供核心的自动化对象的指针`Project`接口，该已实现接口。  
  
 以下是的语法`IVsHierarchy::GetProperty`。  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 项目适应嵌套和使用集合来创建的项目项的组。 层次结构如下所示。  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 嵌套意味着<xref:EnvDTE.ProjectItem>对象可以是<xref:EnvDTE.ProjectItems>同时集合因为`ProjectItems`集合可以包含嵌套的对象。 基本项目示例不演示此嵌套。 通过实现`Project`对象，参与的总体的自动化模型设计的特点是类似于树的结构。  
  
 项目自动化遵循下图中的路径。  
  
 ![Visual Studio 项目对象](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
项目自动化  
  
 如果你未实现`Project`对象，则环境仍将返回泛型`Project`对象，其中包含仅项目的名称。  
  
## <a name="see-also"></a>另请参阅  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>