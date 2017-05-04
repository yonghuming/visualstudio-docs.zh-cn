---
title: "&lt;document&gt; 元素（Visual Studio 中的 Office 开发） | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "document 元素"
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<document> 元素"
  - "<document> 元素"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;document&gt; 元素（Visual Studio 中的 Office 开发）
  `vstov4` 命名空间的 `document` 元素存储文档级自定义项的自定义项特定信息。  
  
## 语法  
  
```  
<document solutionId />  
```  
  
## 元素和特性  
 仅对文档级自定义项是必需的。  `document` 元素在 `vstov4` 命名空间中。  `document` 元素具有以下特性。  
  
|特性|说明|  
|--------|--------|  
|`solutionId`|必选。  for Office runtime 的 Visual Studio 工具使用的 GUID 唯一地标识一个文档级解决方案。  此值存储为 \_AssemblyLocation 自定义文档属性。  有关更多信息，请参见[自定义文档属性概述](../vsto/custom-document-properties-overview.md)。|  
  
 `document` 没有子元素。  
  
## 文档级自定义项示例  
  
### 说明  
 下面的代码示例演示文档级 Office 解决方案的 `document`元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。  此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  