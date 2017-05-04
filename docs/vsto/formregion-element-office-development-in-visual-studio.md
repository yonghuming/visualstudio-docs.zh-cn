---
title: "&lt;formRegion&gt; 元素（Visual Studio 中的 Office 开发） | Microsoft Docs"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<formRegion> 元素"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;formRegion&gt; 元素（Visual Studio 中的 Office 开发）
  `vstov4`  命名空间的 `formRegion` 元素标识与 VSTO 外接程序关联的 Microsoft Office Outlook 窗体区域。  
  
## 语法  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## 元素和属性  
 `vstov4`  命名空间的 `formRegion` 元素标识与 Outlook VSTO 外接程序关联的窗体区域。 只有包括窗体区域的 Outlook VSTO 外接程序才需要该元素。  
  
 单个 VSTO 外接程序的一个 `formRegions` 元素中可以定义多个 `formRegion` 元素。  
  
 `formRegion` 元素具有以下属性。  
  
|特性|描述|  
|--------|--------|  
|`name`|必需。 标识窗体区域名称。|  
  
 `formRegion` 元素具有以下子元素。  
  
### messageClass  
 `messageClass`  元素标识与窗体区域关联的 Outlook 窗体。  
  
 `messageClass` 元素具有以下属性。  
  
|特性|说明|  
|--------|--------|  
|`name`|必需。 标识与窗体区域关联的窗体。|  
  
## 示例  
 下面的代码示例阐释 Outlook VSTO 外接程序的应用程序清单中的 `formRegion` 元素，该外接程序是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 其中有三个邮件类与这一个窗体区域关联。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## 请参阅  
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  