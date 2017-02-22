---
title: "&lt;description&gt; 元素（ClickOnce 部署） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> 元素 [ClickOnce 部署清单]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;description&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识用于创建 shell 表示和控件面板中**“添加或删除程序”**项的应用程序信息。  
  
## 语法  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## 元素和特性  
 `description` 元素是必需的，它位于 `urn:schemas-microsoft-com:asm.v1` 命名空间中。  它不包含任何子元素，且具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`publisher`|必选。  当进行针对安装的部署配置时，标识 Windows 的**“开始”**菜单和控件面板中的**“添加或删除程序”**项中用于图标所在位置的公司名称。|  
|`product`|必选。  标识产品的全称。  用作安装在 Windows**“开始”**菜单中的图标的标题。|  
|`suiteName`|可选。  标识 Windows**“开始”**菜单中 `publisher` 文件夹内的子文件夹。|  
|`supportUrl`|可选。  指定显示在控制面板的**“添加或删除程序”**项中的支持 URL。  当部署配置为安装时，还可以为 Windows**“开始”**菜单中的应用程序支持创建此 URL 的快捷方式。|  
  
## 备注  
 在所有部署配置中，description 元素都是必需的。  
  
## 示例  
 下面的代码示例阐释了 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署清单中的 `description` 元素。  此代码示例摘自为 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题提供的一个更大示例。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## 请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)