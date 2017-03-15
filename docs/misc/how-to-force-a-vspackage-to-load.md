---
title: "如何：强制 VSPackage 加载 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage，强制加载"
  - "Vspackage，加载"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# 如何：强制 VSPackage 加载
，才需要它们附带的功能完成处理时， Vspackage 通常会加载。  在某些情况下，但是，一些可能必须强制另一个 VSPackage 加载。  例如，轻量级 VSPackage 可能在不能用作 CMDUIContext 的一种编程上下文中更大的 VSPackage。  
  
 可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> 方法强制 VSPackage 加载。  
  
### 强制 VSPackage 加载  
  
-   插入此代码来强制另一个 VSPackage 加载 VSPackage 中 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法中:  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     在 VSPackage 初始化，则将强制 `PackageToBeLoaded` 加载。  
  
## 可靠编程  
 不应使用 VSPackage 通信使用强制加载。  请改用 [使用并提供服务](../extensibility/using-and-providing-services.md)。  
  
## 请参阅  
 [管理 Vspackage](../extensibility/managing-vspackages.md)   
 [Vspackage](../extensibility/internals/vspackages.md)