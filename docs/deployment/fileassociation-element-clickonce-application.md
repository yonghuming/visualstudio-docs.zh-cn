---
title: "&lt;fileAssociation&gt; 元素（ClickOnce 应用程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<fileAssociation> 元素 [ClickOnce 应用程序清单]"
  - "清单 [ClickOnce], fileAssociation 元素"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;fileAssociation&gt; 元素（ClickOnce 应用程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识要与应用程序关联的文件扩展名。  
  
## 语法  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## 元素和特性  
 `fileAssociation` 元素是可选的。  它具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`extension`|必选。  与应用程序关联的文件扩展名。|  
|`description`|必选。  shell 使用的文件类型的说明。|  
|`progid`|必选。  用于唯一地标识文件类型的名称。|  
|`defaultIcon`|必选。  指定用于带有此扩展名的文件的图标。  必须在包含此元素的 [\<assembly\> 元素](../deployment/assembly-element-clickonce-application.md)内使用 [\<file\> 元素](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)指定图标文件。|  
  
## 备注  
 此元素必须包括指向“urn:schemas\-microsoft\-com:clickonce.v1”的 XML 命名空间引用。  如果使用 `<fileAssociation>` 元素，则必须将其放置在父级 [\<assembly\> 元素](../deployment/assembly-element-clickonce-application.md)内的 `<application>` 元素的后面。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将不会重写现有文件关联。  然而，ClickOnce 应用程序只有对当前用户才可以重写文件扩展名。  卸载该 ClickOnce 应用程序后，ClickOnce 将删除用户的文件关联，并且每台计算机的关联会再次处于活动状态。  
  
## 示例  
 下面的代码示例演示使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的文本编辑器应用程序的应用程序清单中的 `fileAssociation` 元素。  此代码示例还包括 `defaultIcon` 特性所需的 [\<file\> 元素](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)。  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## 请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)