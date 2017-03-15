---
title: "使用托管的包框架为一种项目类型 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 1d70a70b942b3722ed61e1e8a2f2e54d96b916e4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>使用托管的包框架来实现一种项目类型 (C#)
管理包框架 (MPF) 提供了 C# 类可以使用或继承来实现您自己的项目类型。 MPF 实现许多 Visual Studio 期望项目类型以提供，这些接口使您可以将集中精力实现您的项目类型的细节。  
  
## <a name="using-the-mpf-project-source-code"></a>使用 MPF 项目源代码  
 对于项目 (MPFProj) 管理软件包框架提供了用于创建和管理新的项目系统的帮助器类。 与 MPF 中的其他类，不同的程序集随 Visual Studio 中不包括项目类。 相反，以在源代码的形式提供了项目类[项目 2013年的 MPF](http://mpfproj12.codeplex.com)。  
  
 若要将此项目添加到 VSPackage 解决方案，请执行以下操作︰  
  
1.  将 MPFProj 文件下载到*MPFProjectDir*。  
  
2.  在*MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file，更改以下块︰  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  创建 VSPackage 项目。  
  
2.  卸载 VSPackage 项目。  
  
3.  VSPackage.csproj 文件编辑通过添加以下块之前另`<Import>`块︰  
  
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
  
2.  关闭并重新打开 VSPackage 解决方案中。  
  
3.  重新打开 VSPackage 项目。 您应该看到一个名为 ProjectBase 的新目录。  
  
4.  将添加到 VSPackage 项目的以下引用︰  
  
     Microsoft.Build.Tasks.4.0  
  
5.  生成项目。  
  
## <a name="hierarchy-classes"></a>层次结构类  
 下表汇总了支持项目层次结构中 MPFProj 的类。 有关详细信息，请参阅[层次结构和所选内容](../../extensibility/internals/hierarchies-and-selection.md)。  
  
|类名称|  
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
 下表列出支持的类 MPF 中的文档处理。 有关详细信息，请参阅[打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
|类名称|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>配置和输出类  
 下表列出 MPF，使项目类型支持多个配置，如调试和发布和项目输出集合中的类。 有关详细信息，请参阅[管理配置选项](../../extensibility/internals/managing-configuration-options.md)。  
  
|类名称|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>自动化支持类  
 下表列出支持自动化，以便您的项目类型的用户可以编写加载项中 MPF 的类。  
  
|类名称|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>属性类  
 下表列出了 MPF，使项目类型中的类添加属性，用户可以浏览和修改属性浏览器中。  
  
|类名称|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
