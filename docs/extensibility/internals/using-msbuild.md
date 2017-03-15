---
title: "使用 MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages，用 MSBuild 编译"
  - "MSBuild，可扩展性"
  - "用 MSBuild 编译的包"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 使用 MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild 提供了用于创建全面地描述项目项来生成、 生成任务，和生成配置的项目文件以定义完善的、 可扩展 XML 格式。  
  
 有关基于 MSBuild 的语言项目系统的端到端示例，请参阅 IronPython 示例中的深入了解[VSSDK 示例](../../misc/vssdk-samples.md)。  
  
## 常规 MSBuild 注意事项  
 MSBuild 项目文件，例如， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj 文件包含在生成时使用，但也可以包含在设计时使用的数据的数据。 生成时数据存储使用 MSBuild 基元，包括 [Item 元素 \(MSBuild\)](../../msbuild/item-element-msbuild.md) 和 [Property 元素 \(MSBuild\)](../../msbuild/property-element-msbuild.md)。 设计时数据，这是特定于项目类型和任何相关的项目子类型的数据，存储在为其保留的自由格式 XML。  
  
 MSBuild 不具有对配置对象的本机支持，但提供了用于指定特定于配置的数据条件属性。 例如：  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 条件属性的详细信息，请参阅 [条件构造](../../msbuild/msbuild-conditional-constructs.md)。  
  
### 针对您的项目类型扩展 MSBuild  
 MSBuild 界面和 Api 可能会有所更改的未来版本中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，它是比较明智的做法是，若要使用的托管的包 framework \(MPF\) 类，因为它们提供屏蔽的更改。  
  
 对于项目 \(MPFProj\) 管理软件包框架提供了用于创建和管理新的项目系统的帮助器类。 您可找到源在代码和编译指令 [项目\-Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 特定于项目的 MPF 类如下所示︰  
  
|类|实现|  
|-------|--------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` 类是 MSBuild 项的包装器。  
  
#### 单文件生成器 vs。MSBuild 任务  
 单个文件生成器是设计时，才可访问但 MSBuild 任务可以使用在设计时和生成时间。 最大的灵活性，因此，使用 MSBuild 任务可以使用转换和生成代码。 有关更多信息，请参见[自定义工具](../../extensibility/internals/custom-tools.md)。  
  
## 请参阅  
 [MSBuild 参考](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/zh-cn/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [自定义工具](../../extensibility/internals/custom-tools.md)