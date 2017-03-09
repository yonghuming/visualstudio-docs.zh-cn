---
title: "安装和部署常见问题 | Microsoft Docs"
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
  - "部署 [Visual Studio SDK]"
  - "LCID [Visual Studio SDK]"
  - "安装 [Visual Studio SDK]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 安装和部署常见问题
本主题建议从 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 用户相关的问题有关安装和部署。  主题将继续更新与从社区的新目录。  
  
## 内容  
  
-   [确定 Visual Studio 安装的 LCID 程序模型](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> 确定 Visual Studio 安装的 LCID 程序模型  
 **Q:** 是否有编程方式确定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安装的 LCID?  
  
 **A:**  <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A>将返回当前正在使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 LCID。  
  
## 请参阅  
 [发布产品](../misc/releasing-a-visual-studio-integration-product.md)