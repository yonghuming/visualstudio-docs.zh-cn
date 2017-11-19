---
title: "项目类型 (C#) 使用托管的包框架 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16e1d301e5a3977f656c52f9c97eb43ee216075f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>使用托管的包框架来实现一种项目类型 (C#)
托管包框架 (MPF) 提供 C# 类可以使用或继承自实现您自己的项目类型。 MPF 实现许多 Visual Studio 期望项目类型以提供，接口使您可以将精力实现特定的你的项目类型。  
  
## <a name="using-the-mpf-project-source-code"></a>使用 MPF 项目源代码  
 托管包框架，用于项目 (MPFProj) 提供用于创建和管理新的项目系统的帮助器类。 与 MPF 中的其他类，不同的项目类不包括在随 Visual Studio 一起提供的程序集。 相反，以在源代码的形式提供了项目类[项目 2013年的 MPF](http://mpfproj12.codeplex.com)。  
  
 若要将此项目添加到你的 VSPackage 的解决方案，请执行以下操作：  
  
1.  下载到 MPFProj 文件*MPFProjectDir*。  
  
2.  在*MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file，更改以下块：  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  创建 VSPackage 项目。  
  
2.  卸载 VSPackage 项目。  
  
3.  VSPackage.csproj 文件编辑通过添加以下块之前另`<Import>`块：  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  保存项目。  
  
2.  关闭并重新打开 VSPackage 解决方案。  
  
3.  重新打开 VSPackage 项目。 你应看到一个名为 ProjectBase 的新目录。  
  
4.  添加到 VSPackage 项目以下引用：  
  
     Microsoft.Build.Tasks.4.0  
  
5.  生成项目。  
  
## <a name="hierarchy-classes"></a>层次结构类  
 下表总结了支持项目层次结构中 MPFProj 的类。 有关详细信息，请参阅[层次结构和选择](../../extensibility/internals/hierarchies-and-selection.md)。  
  
|类名|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>文档处理类  
 下表列出支持文档处理中 MPF 的类。 有关详细信息，请参阅[打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
|类名|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>配置和输出类  
 下表列出 MPF，使项目类型支持多个配置，例如调试和发布、 和的项目输出集合中的类。 有关详细信息，请参阅[管理配置选项](../../extensibility/internals/managing-configuration-options.md)。  
  
|类名|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>自动化支持类  
 下表列出支持自动化，因此，你的项目类型的用户可以编写外接程序中 MPF 的类。  
  
|类名|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>属性类  
 下表列出 MPF，使项目类型中的类添加用户可以浏览和修改属性浏览器中的属性。  
  
|类名|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|