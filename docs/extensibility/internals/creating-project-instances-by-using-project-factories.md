---
title: "通过使用项目工厂来创建项目实例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目工厂"
  - "项目 [Visual Studio SDK]，项目工厂"
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 通过使用项目工厂来创建项目实例
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目输入 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 *项目工厂* 创建项目对象实例。  项目工厂类似于 cocreatable COM 对象的标准类工厂。  但是，项目对象不 cocreatable:使用项目工厂，才能创建。  
  
 ，当用户在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]时，加载现有项目或创建新项目 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 在 VSPackage 称为项目工厂实现。  新项目对象提供 IDE 提供足够的信息在解决方案资源管理器中。  新项目对象支持 IDE 启动的所有相关 UI 操作还提供必需的接口。  
  
 可以在类中实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 接口在项目。  通常，它位于各自的模块。  
  
 有关 `IVsProjectFactory` 接口的实现的示例，请参见。 [Basic Project](http://msdn.microsoft.com/zh-cn/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) 示例目录包含的 PrjFac.cpp。  
  
 支持聚合由所有者的项目在它们的项目文件必须保持所有者键。  当 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 调用方法与所有者键项目时，则拥有的项将其所有者键为项目 factory GUID 调用此项目工厂的 `CreateProject` 方法执行实际创建。  
  
## 创建一个拥有的项目  
 所有者在两个阶段中创建一个拥有的项:  
  
1.  通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> 方法。  这使该项目拥有的机会创建基于输入的一个复合项目的对象控制 `IUnknown`。  该拥有的项目通过内部 `IUnknown` 和聚合的对象返回所有者项目。  这使该项目拥有的机会存储内部 `IUnknown`。  
  
2.  通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> 方法。  该拥有的项目实现其所有实例化，当调用此方法而不是调用 `IVsProjectFactory::CreateProject` 不属于项目的大小写。  输入 `VSOWNEDPROJECTOBJECT` 枚举通常是该聚合拥有的项目。  该拥有的项目使用此变量确定其项目对象是否已创建 \(cookie 不等于空\) 或必须创建 \(cookie 等于空\)。  
  
 项类型由单个项目 GUID 标识，类似于一 cocreatable COM 对象的 CLSID。  通常，创建一个项类型的实例的项目工厂处理，不过，有一项工厂处理多个项目类型 GUID 是可能的。  
  
 项类型与特定文件关联扩展名。  当用户尝试打开一个现有项目文件或尝试通过克隆模板创建新项目时， IDE 使用该文件的扩展名确定相应的项目 GUID。  
  
 当 IDE 确定它是否必须创建新项目或打开特定类型的现有项目， IDE 在系统注册表使用下的信息 \[HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\8.0\\Projects\] to find which VSPackage 实现必需的项工厂。  IDE 加载此 VSPackage。  在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 方法， VSPackage 通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> 方法必须注册其 IDE 会项目工厂。  
  
 `IVsProjectFactory` 接口的主要方法是的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 如果处理两方案:打开现有项目并创建新的项目。  大多数在项目文件中存储其项目的状态。  通常，新项目是通过复制模板文件传递给 `CreateProject` 方法然后打开复制创建的。  现有项目通过直接打开项目文件实例化传递给 `CreateProject` 方法。  `CreateProject` 方法可以根据需要显示附加 UI 功能给用户。  
  
 除文件系统外，例如数据库或 Web 服务器，项目在存储机制不能使用文件，因此，相反，存储其项目状态。  在这种情况下，文件名参数传递给 `CreateProject` 方法实际上不是文件系统路径，但单个字符串的 URL 标识项数据。  您不需要复制传递给 `CreateProject` 触发将执行适当的构造序列的模板文件。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)