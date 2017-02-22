---
title: "注册 Vspackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "托管的 VSPackages 注册"
  - "注册、 托管的 VSPackages"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 注册 Vspackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 依赖于 .pkgdef 文件描述和查找 VSPackage。  .pkgdef 文件包含在其他情况下添加到系统注册表的所有注册信息。  托管 Vspackage 通过将特性添加到源代码然后运行在生成的程序集的 [CreatePkgDef 实用程序](../../extensibility/internals/createpkgdef-utility.md) 生成 .pkgdef 文件中注册。  
  
## 本节内容  
 [指定到 VS Shell VSPackage 文件位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 描述 Vspackage 的加载路径。  
  
 [注册和注销 VSPackages 迁移](../../extensibility/registering-and-unregistering-vspackages.md)  
 说明如何注册 VSPackage。  
  
 [使用自定义注册特性注册扩展](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)  
 描述如何创建可用于部署管理的 VSPackage 不同的注册。