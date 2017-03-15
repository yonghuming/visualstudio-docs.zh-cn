---
title: "状态持久性支持 | Microsoft Docs"
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
  - "状态持久性, 托管包框架支持"
  - "托管包框架, 状态持久性支持"
  - "状态, 持久性"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# 状态持久性支持
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 维护常用对象的状态。  例如，解决方案和项目属性来保存到并从解决方案和项目文件中恢复。  用户可导出到和从一组文件导入。  
  
 Vspackage 通常依赖于本地存储区，在系统注册表或应用 data 文件夹的当前用户或计算机。  用于存储需要少量空间，如整数和字符串的值，在系统注册表通常存储。  用于存储需要过多的空间，如位图的值，则在文件中。  文件的路径在系统注册表本身可以保存。  保持机制必须有权访问本地存储区。  
  
## 为找到本地存储区支持  
 <xref:Microsoft.VisualStudio.Shell.Package> 类提供查找状态信息以支持当前用户或计算机上的系统注册表或应用程序数据 " 文件夹。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 返回本地计算机上的注册表的路径支持 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如， HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\8.0Exp。  
  
 本地注册表根从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 服务来获取。  如果这是可用，它将从 VSPackage 中 <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> 属性获取的。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 返回当前用户的 \(每台计算机\) 注册表的路径支持 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如， HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0Exp。  
  
 本地注册表根从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 服务来获取。  如果这是可用，它将从 VSPackage 中 DefaultLocalRegistryRoot 属性获取的。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 返回字符串通用储存库当前漫游用户的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 数据，例如， C 根目录的路径: \\Documents and Settings \\*TheAccountName*\\Application Data\\Microsoft\\VisualStudio\\8.0Exp。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 返回字符串通用储存库当前非漫游用户的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 数据，例如， C 根目录的路径: \\Documents and Settings \\*TheAccountName*\\Local Settings\\Application Data\\Microsoft\\VisualStudio\\8.0Exp。  
  
## 请参阅  
 [VSPackage 状态](/visual-cpp/misc/vspackage-state)