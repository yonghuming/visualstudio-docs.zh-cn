---
title: "&lt;update&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "update 元素"
  - "<update> 元素"
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<update> 元素"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# &lt;update&gt; 元素（Visual Studio 中的 Office 开发）
  `update` 元素指定解决方案检查更新的间隔。  
  
## 语法  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## 元素和特性  
 需要 `update` 元素并在 `vstav3` 命名空间。  
  
 `update` 元素具有以下特性。  
  
|特性|说明|  
|--------|--------|  
|`enabled`|必需。  enabled 可设置为下列值之一:<br /><br /> -   检查的**TRUE** 更新。<br />-   阻止的**FALSE** 检查更新。|  
  
 `update` 元素具有以下子元素。  
  
### 过期  
 需要 `expiration` 元素并在 `vstav3` 命名空间。  此元素指定解决方案检查更新的间隔。  
  
 `expiration` 元素具有以下特性。  
  
|特性|说明|  
|--------|--------|  
|`maximumAge`|-   必需。  设置为一个整数。|  
|`unit`|必需。  设置 `unit` 为下列值之一:<br /><br /> -   **小时**<br />-   **天数**<br />-   **weeks**|  
  
## 始终检查更新的示例  
  
### 说明  
 下面的代码示例演示将总是检查在 Office 解决方案的更新该 `update` 元素。  
  
### 代码  
  
```  
<vstav3:update enabled="true" />  
```  
  
## 设置默认更新间隔的示例  
  
### 说明  
 下面的代码示例演示应用程序清单中的一个 `update` 元素向 Office 解决方案。  此代码示例摘自中提供的一个更大的示例。 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)  
  
### 代码  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## 请参阅  
 [使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  