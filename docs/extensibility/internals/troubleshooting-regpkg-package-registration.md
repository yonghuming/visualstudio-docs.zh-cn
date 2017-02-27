---
title: "疑难解答 RegPkg 包注册 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 疑难解答 RegPkg 包注册
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  在 Visual Studio 中注册包的首选的方式是使用.pkgdef 文件。 这样可以扩展部署而无需访问系统注册表。 通过使用创建 Pkgdef 文件 [CreatePkgDef 实用程序](../../extensibility/internals/createpkgdef-utility.md)。  
  
 若要通过使用在 RegPkg 注册包 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，您必须使用适用于您的软件包的 RegPkg 的版本。  
  
## RegPkg 版本相关的包版本  
 有两个版本的 RegPkg。 中包括一个版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 使用此版本注册通过使用以下程序集之一生成的包:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 它不能注册通过使用早期 Microsoft.VisualStudio.Shell.dll 程序集生成的包。  
  
 使用早期版本的 RegPkg 可以注册通过使用 Microsoft.VisualStudio.Shell.dll 的程序集生成的包。 但是，它不能注册包使用该程序集的更高版本生成的。  
  
## 请参阅  
 [发布产品](../../misc/releasing-a-visual-studio-integration-product.md)