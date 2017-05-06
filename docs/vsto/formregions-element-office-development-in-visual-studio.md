---
title: "&lt;formRegions&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "formRegions 元素"
  - "<formRegions> 元素"
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<formRegions> 元素"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;formRegions&gt; 元素（Visual Studio 中的 Office 开发）
  `vstov4` 命名空间的 `formRegions` 元素包含与 VSTO 外接程序相关联的 Microsoft Office Outlook 窗体区域。  
  
## 语法  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## 元素和属性  
 `vstov4` 命名空间的 `formRegions` 元素包含 Outlook VSTO 外接程序的所有 `formRegion` 元素。 只有包括窗体区域的 Outlook VSTO 外接程序才需要该元素。  
  
 在应用程序清单中定义的 `formRegions` 元素可能只有一个。  
  
 `formRegions` 元素没有属性。  
  
 `formRegions` 元素具有以下元素。  
  
### formRegion  
 为包含窗体区域的 Outlook VSTO 外接程序所需。`formRegion` 元素定义在 [&#60;formRegion&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/formregion-element-office-development-in-visual-studio.md) 中。  
  
## VSTO 外接程序示例  
  
### 说明  
 下面的代码示例演示应用程序级 Office 解决方案的应用程序清单中的 `formRegions` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  