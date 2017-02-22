---
title: "项目模型的元素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [Visual Studio SDK]，实现注意事项"
  - "项目模型"
  - "项目 [Visual Studio SDK] 元素"
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 项目模型的元素
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

所有项目的接口和实现。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的共享一个基本结构:项类型的项目模型。  在项目模型，这是 VSPackage 您开发，您创建符合设计决策和使用 IDE 提供的全局函数一起的对象。  虽然您可以控制项目项，例如，如何保持不控件通知必须保持文件。  当用户值一个打开的项目项并选择。 **文件** 菜单的 **保存** 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 菜单栏时，项目类型代码必须截获从 IDE 的命令，保存文件，并将注意到 IDE 不再更改文件。  
  
 VSPackage 来与 IDE 进行交互。提供对 IDE 接口的服务。  例如，通过特定服务，您监视和路由命令可为该项目所做的选择提供上下文信息。  为 VSPackage 需的任何全局 IDE 功能由服务提供。  有关服务的更多信息，请参见 [如何: 获取服务](../Topic/How%20to:%20Get%20a%20Service.md)。  
  
 其他实现注意事项:  
  
-   单个项目模型可以包含多个项目类型。  
  
-   项类型以及伴随项目工厂独立向 GUID 注册。  
  
-   ，当用户通过 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI 时，会创建一个新的项目每个项目必须具有初始化模板文件或的向导新项目文件。  例如， [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 模板初始化的最终成为 .vcproj 文件。  
  
 下面的插图显示了组成一种典型的项目中实现的主要接口、服务以及对象。  您可以使用应用程序帮助器， HierUtil7，创建基础对象和其他编程的样本。  有关 HierUtil7 应用程序帮助器的更多信息，请参见 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/zh-cn/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
 ![Visual Studio 项目模型图](../../extensibility/internals/media/vsprojectmodel.png "vsProjectModel")  
项目模型  
  
 有关在上图中和服务列表的接口以及在关系图中未包含的其他选项接口的更多信息，请参见 [项目模型核心组件](../../extensibility/internals/project-model-core-components.md)。  
  
 项目支持命令并且必须实现接口 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 参与命令传送通过命令上下文 GUID。  
  
## 请参阅  
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/zh-cn/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [项目模型核心组件](../../extensibility/internals/project-model-core-components.md)   
 [通过使用项目工厂来创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [如何: 获取服务](../Topic/How%20to:%20Get%20a%20Service.md)   
 [创建项目类型](../../extensibility/internals/creating-project-types.md)