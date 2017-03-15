---
title: "将 Web 服务添加到项目系统 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目系统, 添加 Web 服务"
  - "Web 服务, 添加到 VSPackage 项目系统"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# 将 Web 服务添加到项目系统
XML web services 是，通常，使用 SOAP 的 URL 可寻址的资源 \(简单对象访问协议\) 协议，返回编程信息对项目系统。  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> 接口，您可以将 web 服务添加到 VSPackage 项目系统。  
  
### 将 web 服务添加到项目系统  
  
1.  通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> 服务调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> 接口的 `QueryService` 。  
  
2.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 方法。  如果在 `pDiscoverySession` 参数将作为 `NULL`，查看会话已为您创建，并且，缓存会议，使其可供后续使用由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> 接口。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 方法返回指向 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>。  
  
3.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> 方法。  在自动化对象的通过 web 服务的引用 " 文件夹作为 `pUnkWebReferenceFolder` 参数。  Visual Studio 环境然后检查 web 服务是否已存在。  如果 web 服务不存在，该环境下载并将 web 服务添加到文件夹和任何其他文件 \(例如 .wsdl 文件\) 添加到该文件夹的子节点。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>