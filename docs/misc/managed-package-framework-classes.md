---
title: "托管包框架类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "托管包框架，帮助程序类"
  - "托管包帮助程序类"
  - "Visual Studio SDK，托管包帮助程序类"
  - "类 [Visual Studio SDK]，托管包框架"
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# 托管包框架类
使用托管代码，托管包框架 \(MPF\) 类可以用于创建 Vspackage。 它们提供许多 VSPackage 接口的默认实现。 通过隐藏实现细节和复杂性，MPF 使你能够利用最少量的代码创建 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成产品。  
  
> [!WARNING]
>  大多包含托管包框架类的程序集都附带有 Visual Studio SDK。 可以在[项目的托管包框架](http://mpfproj11.codeplex.com/)下载适用于项目 的托管包框架的源代码。  
  
## MPF 命名空间  
 下表列出了由 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 提供的 MPF 命名空间。  
  
|命名空间|内容|  
|----------|--------|  
|<xref:Microsoft.VisualStudio>|包含用于处理 COM 错误、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 常量和 Win32 窗口的有用类。|  
|<xref:Microsoft.VisualStudio.Package>|包含 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目、编辑器和 MSBuild 的托管代码包装。|  
|<xref:Microsoft.VisualStudio.Shell>|包含可从其派生许多常见 Visual Studio 对象的实现的 MPF 基类。|  
|<xref:Microsoft.VisualStudio.Shell.Design>|包含 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设计器扩展。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|包含 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 序列化设计器扩展。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|包含 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CodeDom 设计器扩展。|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|支持项目子类型（也称为“风格”）。|  
  
## 请参阅  
 [VSPackage 和托管包框架](/visual-cpp/misc/vspackages-and-the-managed-package-framework)   
 [使用 Visual Studio 互操作程序集](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackage 和托管包框架](/visual-cpp/misc/vspackages-and-the-managed-package-framework)