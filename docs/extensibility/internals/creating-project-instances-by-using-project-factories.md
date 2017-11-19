---
title: "使用项目工厂创建项目实例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7175bd4e2d0b07640dd45b38aa246c649def32ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-instances-by-using-project-factories"></a>使用项目工厂创建项目实例
中的项目类型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用*项目工厂*创建的项目对象实例。 项目工厂是类似于 cocreatable COM 对象的标准类工厂。 但是，项目对象不是 cocreatable： 仅可以通过使用项目工厂创建它们。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 调用用户加载现有项目或创建一个新项目中的时，在你的 VSPackage 中实现的项目工厂[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 新的项目对象提供具有足够的信息的 IDE 来填充解决方案资源管理器。 新的项目对象还为支持所有相关的 UI 操作由 IDE 提供所需的接口。  
  
 你可以实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>中你的项目中的类接口。 通常情况下，它在位于其自己的模块。  
  
 有关实现的示例`IVsProjectFactory`接口，请参阅中包含的 PrjFac.cpp[基本项目](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36)示例目录。  
  
 支持聚合的所有者的项目必须保留其项目文件中的所有者密钥。 当<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>具有所有者键项目调用方法、 拥有的项目将其所有者键转换为 GUID 然后调用一个项目工厂`CreateProject`来进行实际创建此项目工厂方法。  
  
## <a name="creating-an-owned-project"></a>创建一个拥有的项目  
 所有者在两个阶段创建的所有的项目：  
  
1.  通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>方法。 这给拥有的项目以创建在输入控制基于聚合的项目对象一个机会`IUnknown`。 拥有的项目将传递内部`IUnknown`和回所有者项目的聚合的对象。 这使拥有的项目存储内部有机会`IUnknown`。  
  
2.  通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>方法。 此方法调用而不是调用时，拥有的项目将执行所有其实例化`IVsProjectFactory::CreateProject`会出现不拥有的项目的情况。 输入`VSOWNEDPROJECTOBJECT`枚举通常是聚合拥有的项目。 拥有的项目可以使用此变量来确定是否已创建其项目对象 （cookie 不等于 NULL） 或必须创建 （cookie 等于 NULL）。  
  
 项目类型进行标识的唯一项目 GUID，类似于 cocreatable 的 COM 对象的 CLSID。 通常，一个项目工厂句柄创建单个项目类型的实例，但也可以具有一个项目工厂可处理多个项目类型 GUID。  
  
 项目类型都与特定文件扩展名关联。 当用户尝试打开现有的项目文件，或尝试通过克隆模板创建新项目时，IDE 会使用的文件扩展名来确定相应项目 GUID。  
  
 只要 IDE 确定是否它必须创建一个新项目或打开现有项目的特定类型，IDE 使用信息在系统注册表项下 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] 来找出哪些VSPackage 实现所需的项目工厂。 IDE 将加载此 VSPackage。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>方法，VSPackage 必须将注册其项目工厂 IDE 通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>方法。  
  
 主要方法`IVsProjectFactory`接口是<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>这应处理两种方案： 打开现有项目并创建新的项目。 大多数项目在项目文件中存储其项目状态。 通常情况下，新项目将创建的模板文件的副本传递给`CreateProject`方法，并打开副本。 直接打开项目文件传递到现有的项目进行实例化由`CreateProject`方法。 `CreateProject`方法可以向用户根据需要显示其他 UI 功能。  
  
 一个项目都可以还使用任何文件，并将其项目状态相反，存储在文件系统，例如数据库或 Web 服务器以外的存储机制。 在这种情况下，文件名称参数传递给`CreateProject`方法不是实际的文件系统路径，而一个唯一字符串-URL-标识项目数据。 不需要将传递给模板文件复制`CreateProject`触发要执行的适当构造序列。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [清单：新建项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)