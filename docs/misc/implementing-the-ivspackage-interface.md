---
title: "实现 IVsPackage 接口 | Microsoft Docs"
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
  - "IVsPackage 接口"
  - "接口, 实现 IVsPackage"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 实现 IVsPackage 接口
所有 Vspackage 必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 接口。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 初始化并关闭的 Vspackage， get 方法关联的属性页和出于其他原因。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 接口是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 VSPackage 之间的通道接口。  
  
 可以编写托管 VSPackage 作为 <xref:Microsoft.VisualStudio.Shell.Package> 类的子类，实现委托的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 。  有关更多信息，请参见 [托管的 VSPackage](../misc/managed-vspackages.md)。  
  
> [!NOTE]
>  许多在 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 的 Visual Studio 集成部分的非托管代码示例使用 \(ATL\)活动模板库 \(atl\)。  无需使用 ATL 创建 Vspackage，但是，您必须了解 ATL 了解代码示例。  
  
## 请参阅  
 [Vspackage](../extensibility/internals/vspackages.md)