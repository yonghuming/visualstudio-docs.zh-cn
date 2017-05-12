---
title: "&lt;vstoRuntime&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<vstoRuntime> 元素"
  - "<vstoRuntime> 元素"
  - "vstoRuntime 元素"
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# &lt;vstoRuntime&gt; 元素（Visual Studio 中的 Office 开发）
  `vstav3`  命名空间的 `vstoRuntime` 元素包含针对特定 Office 解决方案的受支持的 Visual Studio Tools for Office Runtime 版本。  
  
## 语法  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## 元素和属性  
 `vstoRuntime` 元素是必需的，它位于 `vstav3`  命名空间中。 如果 Office 解决方案支持两个版本的 Visual Studio Tools for Office Runtime，则应用程序清单中存在两个 `vstoRuntime` 元素。  
  
 `vstoRuntime` 元素具有以下属性。  
  
|特性|说明|  
|--------|--------|  
|`release`|必需。 Visual Studio Tools for Office Runtime 的发布版本。|  
|`version`|必需。 Visual Studio Tools for Office Runtime 的版本号。|  
|`supportUrl`|可选。 指向 Visual Studio Tools for Office Runtime 安装位置的链接。|  
  
 `vstoRuntime` 不包含任何元素。  
  
## 示例  
 下面的代码示例演示 Office 解决方案的应用程序清单中的 `vstoRuntime` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
```  
<vstav3:vstoRuntime release="VSTOR40Beta1" version="10.0.20303" supportUrl="http://www.microsoft.com" />  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  