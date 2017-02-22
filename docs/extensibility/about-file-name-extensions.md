---
title: "有关文件扩展名 | Microsoft Docs"
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
  - "文件扩展名"
  - "文件扩展名"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 有关文件扩展名
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当您注册 VSPackage 的文件扩展名，则将其与 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的版本。  此外，如果多 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 个版本的计算机上，安装这非常重要。  
  
 Vspackage 的文件扩展名注册在使用指向该关联的编程标识符默认值的 HKEY\_CLASSES\_ROOT 项下 \(progid\)。  
  
 下面是注册信息的示例 .vcproj 文件扩展名的:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 文件与 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 必须具有的 ProgID，例如 `VisualStudio.vcproj.8.0`，使产品的并行安装维护在产品版本的文件扩展名关联。  一个特定于版本的 ProgID 还允许您使用标准谓词，如打开，编辑器，依此类推，，而无需 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的其他应用程序或版本复盖或复盖的问题。  
  
 在某些情况下，不应更改 ProgID 与文件扩展名。  例如， .htm 文件扩展名 \(progid ProgID \= htmlfile\) 是硬编码操作系统的线和广泛了解并使用 .htm 和 .html 文件具有关系。  
  
## 请参阅  
 [注册由并行部署的文件扩展名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [指定文件扩展名的文件处理程序](../extensibility/specifying-file-handlers-for-file-name-extensions.md)