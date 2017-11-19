---
title: "使用 MSBuild |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a148a7c5fa6d0e72345ab7f96696a11d5ba5185f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-msbuild"></a>使用 MSBuild
MSBuild 提供了用于创建全面地描述要生成、 生成任务，并生成配置的项目项的项目文件以定义完善的可扩展 XML 格式。  
  
## <a name="general-msbuild-considerations"></a>常规 MSBuild 注意事项  
 MSBuild 项目文件，例如， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj 和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].vbproj 文件包含在生成期间使用，但还可以包含在设计时使用的数据的数据。 生成时数据用 MSBuild 基元，包括存储[Item 元素 (MSBuild)](../../msbuild/item-element-msbuild.md)和[Property 元素 (MSBuild)](../../msbuild/property-element-msbuild.md)。 设计时数据，这是特定于项目类型和任何相关的项目子类型的数据，存储在为其保留的自由格式 XML 中。  
  
 MSBuild 不具有对配置对象的本机支持，但提供了用于指定配置特定数据条件属性。 例如:   
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 条件属性的详细信息，请参阅[条件构造](../../msbuild/msbuild-conditional-constructs.md)。  
  
### <a name="extending-msbuild-for-your-project-type"></a>针对你的项目类型扩展 MSBuild  
 MSBuild 接口和 Api 有所的未来版本中的更改[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，它是比较明智的做法是，若要使用托管的包框架 (MPF) 类，因为它们提供了屏蔽的更改。  
  
 托管包框架，用于项目 (MPFProj) 提供用于创建和管理新的项目系统的帮助器类。 你可找到源代码和编译说明[项目的 Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 特定于项目的 MPF 类如下所示：  
  
|类|实现|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement`类是 MSBuild 项的包装器。  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>单个文件生成器 vs。MSBuild 任务  
 单个文件生成器设计仅在时，可访问，但可以在设计时和生成时使用 MSBuild 任务。 最大的灵活性，因此，使用 MSBuild 任务来转换和生成代码。 有关详细信息，请参阅[自定义工具](../../extensibility/internals/custom-tools.md)。  
  
## <a name="see-also"></a>另请参阅  
 [MSBuild 参考](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [自定义工具](../../extensibility/internals/custom-tools.md)