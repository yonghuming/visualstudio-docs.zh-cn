---
title: "项目模型的元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 689fac97264aad3d301095cffed07b825c723474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="elements-of-a-project-model"></a>项目模型的元素
接口和实现中的所有项目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]共享基本结构： 你的项目类型的项目模型。 在你的项目模型中，这是你正在开发的 VSPackage，你将创建符合你的设计决策和与由 IDE 提供的全局功能一起工作的对象。 尽管您控制如何保持的项目项，例如，在不控制通知必须保留文件。 当用户将焦点置于上打开项目项，并选择**保存**上**文件**上的菜单[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]菜单栏中，你的项目类型代码必须截获 IDE 中的命令，保留文件，和发送通知到 IDE，无法再更改该文件。  
  
 你的 VSPackage 与 IDE 通过提供对 IDE 接口访问的服务进行交互。 例如，通过特定服务，你监视器和路由的命令并提供在项目中所做的选择的上下文信息。 所有全局 IDE 所需的功能为你的 VSPackage 服务所提供的。 有关服务的详细信息，请参阅[如何： 获取服务](../../extensibility/how-to-get-a-service.md)。  
  
 其他实现注意事项：  
  
-   单个项目模型可以包含多个项目类型。  
  
-   向 Guid 独立注册项目类型和助理项目工厂。  
  
-   每个项目必须有一个模板文件或向导来初始化新的项目文件，当用户创建新的项目通过[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI。 例如，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]模板初始化什么最终变得.vcproj 文件。  
  
 下图显示主要接口、 服务和构成典型的项目中实现的对象。 应用程序帮助器，HierUtil7，可用于创建基础对象和其他编程的样本。 HierUtil7 应用程序帮助程序有关的详细信息，请参阅[不在生成中： 使用 HierUtil7 项目类以实现项目类型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
 ![图： visual Studio 项目模型](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
项目模型  
  
 有关接口和列出在上图中，服务以及其他关系图中未包括的可选接口的详细信息，请参阅[项目模型核心组件](../../extensibility/internals/project-model-core-components.md)。  
  
 项目可支持命令，并因此必须实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口以参与命令路由通过命令上下文 Guid。  
  
## <a name="see-also"></a>另请参阅  
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [不在生成中： 使用 HierUtil7 项目类来实现一种项目类型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [项目模型核心组件](../../extensibility/internals/project-model-core-components.md)   
 [使用项目工厂创建项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [如何： 将获得的服务](../../extensibility/how-to-get-a-service.md)   
 [创建项目类型](../../extensibility/internals/creating-project-types.md)