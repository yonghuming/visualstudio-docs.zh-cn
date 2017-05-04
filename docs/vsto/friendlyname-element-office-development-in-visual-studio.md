---
title: "&lt;friendlyName&gt; 元素（Visual Studio 中的 Office 开发） | Microsoft Docs"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<friendlyName> 元素"
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;friendlyName&gt; 元素（Visual Studio 中的 Office 开发）
  `vstov4`  命名空间的 `friendlyName` 元素存储已安装程序列表中出现的名称。  
  
## 语法  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## 元素和属性  
 `friendlyName` 元素位于 `vstov4`  命名空间中。 值出现在计算机中已安装程序列表中和 Microsoft Office 应用程序的 COM VSTO 外接程序对话框中。  
  
 `friendlyName` 元素没有属性或子元素。  
  
## VSTO 外接程序示例  
  
### 说明  
 下面的代码示例演示使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的应用程序级解决方案的 `friendlyName` 元素。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  