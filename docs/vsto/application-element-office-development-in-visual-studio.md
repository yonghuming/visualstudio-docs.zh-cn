---
title: "&lt;application&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<application> 元素"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# &lt;application&gt; 元素（Visual Studio 中的 Office 开发）
  `vstav3` 命名空间的 `application` 元素包装 Office 解决方案的描述。 对于文档级自定义项和 VSTO 外接程序，子元素是不同的。  
  
## 文档级自定义项的语法  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## 应用程序级外接程序的语法  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## 元素和属性  
 `vstav3` 命名空间的 `application` 元素是包装 `vstov4` 命名空间中包含的所有自定义项特定信息的节点。  
  
 `application` 元素没有属性。  
  
 `application` 元素具有以下元素。  
  
### 自定义  
 `vstov3` 命名空间中 `customization` 元素的角色在 [&#60;customization&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/customization-element-office-development-in-visual-studio.md) 中定义。  
  
## 文档级自定义项示例  
  
### 描述  
 下面的代码示例演示使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的文档级 Office 解决方案中的 `application` 元素。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## VSTO 外接程序示例  
  
### 说明  
 以下代码示例演示使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的应用程序级 Office 解决方案中的 `application` 元素。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  