---
title: "选项页的自动化支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具选项页 [Visual Studio SDK]，自动化支持"
  - "自动化 [Visual Studio SDK]，创建工具选项页"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 选项页的自动化支持
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vspackage 可以提供自定义 **选项** 到对话框 **工具** 菜单 \(工具选项页\) 中的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，可以使它们可用于自动化模型。  
  
## 工具选项页  
 若要创建 **工具选项** 页上，VSPackage 必须提供返回到 VSPackage 的实现通过环境的用户控件实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法 \(或托管代码的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法\)。  
  
 它是可选的但强烈建议，以允许访问这一新页面通过自动化模型。 你可以通过以下步骤:  
  
1.  扩展 <xref:EnvDTE._DTE.Properties%2A> 对象，通过 IDispatch 派生的对象的实现。  
  
2.  返回的一个实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法 \(或托管代码的 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 方法\) 对 IDispatch 派生的对象。  
  
3.  当自动化使用者调用 <xref:EnvDTE._DTE.Properties%2A> 方法的自定义 **选项** 属性页中，在环境中使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法来获取自定义 **工具选项** 页面的自动化的实现。  
  
4.  VSPackage 的自动化对象然后用于提供每个 <xref:EnvDTE.Property> 返回 <xref:EnvDTE._DTE.Properties%2A>。  
  
 实现自定义工具选项页的示例，请参阅 [VSSDK 示例](../../misc/vssdk-samples.md)。  
  
## 请参阅  
 [公开项目对象](../../extensibility/internals/exposing-project-objects.md)