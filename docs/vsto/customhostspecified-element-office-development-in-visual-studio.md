---
title: "&lt;customHostSpecified&gt; 元素（Visual Studio 中的 Office 开发） | Microsoft Docs"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<customHostSpecified> 元素"
  - "<customHostSpecified> 元素"
  - "customHostSpecified 元素"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customHostSpecified&gt; 元素（Visual Studio 中的 Office 开发）
  `customHostSpecified` 元素指示此解决方案不是独立应用程序。  Office 解决方案包含 Microsoft Office 应用程序承载的组件。  
  
## 语法  
  
```  
<customHostSpecified />  
```  
  
## 元素和特性  
 `customHostSpecified` 元素对于 Office 解决方案是必需的。  此元素在 `co.v1` 命名空间中，它指定此部署包含将在自定义宿主内部署的组件，并且不是独立应用程序。  
  
 此元素是应用程序清单中第一个 `<entrypoint>` 元素的子元素。  该 `<entrypoint>` 元素中不能存在其他子元素，否则 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 会在安装过程中引发验证错误。  
  
 此元素没有特性，也没有子元素。  
  
## 示例  
 下面的代码示例演示应用程序清单中的 `customHostSpecified` 元素向 Office 解决方案。  此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)中提供的一个更大的示例。  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  