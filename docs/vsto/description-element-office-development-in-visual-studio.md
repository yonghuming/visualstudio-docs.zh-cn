---
title: "&lt;description&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "description 元素"
  - "<description> 元素"
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<description> 元素"
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;description&gt; 元素（Visual Studio 中的 Office 开发）
  `vstov4`  命名空间的 `description` 元素会存储在 Microsoft Office 应用程序的 COM 加载项对话框中显示的 Office 解决方案说明。  
  
## 语法  
  
```  
<description>  
</description>  
```  
  
## 元素和属性  
 可选。`description` 元素位于 `vstov4`  命名空间中。 它包含在 Microsoft Office 应用程序中的 COM 加载项对话框中显示的加载项说明。  
  
 `description` 元素没有属性或元素。  
  
## VSTO 外接程序示例  
  
### 描述  
 下面的代码示例演示使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的应用程序级解决方案的 `description` 元素。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstov4:description> ContosoOutlookAddIn - Outlook add-in created with Visual Studio Tools for Office </vstov4:description>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  