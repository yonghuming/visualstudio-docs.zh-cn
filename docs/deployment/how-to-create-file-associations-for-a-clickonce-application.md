---
title: "如何：为 ClickOnce 应用程序创建文件关联 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce 部署, 文件关联"
  - "文件关联, ClickOnce 应用程序"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：为 ClickOnce 应用程序创建文件关联
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序可以与一个或多个文件扩展名关联，这样当用户打开那些类型的文件时，该应用程序将自动启动。  向 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序添加文件扩展名支持非常简单。  
  
### 为 ClickOnce 应用程序创建文件关联  
  
1.  以常规方式创建一个 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，或者使用现有的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。  
  
2.  用文本编辑器或 XML 编辑器（如“记事本”）打开应用程序清单。  
  
3.  找到 `assembly` 元素。  有关更多信息，请参见 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)。  
  
4.  添加一个 `fileAssociation` 元素，作为 `assembly` 元素的子元素。  `fileAssociation` 元素具有四个特性：  
  
    -   `extension`：要与应用程序关联的文件扩展名。  
  
    -   `description`：文件类型的描述，它将出现在 Windows shell 中。  
  
    -   `progid`：唯一标识文件类型的字符串，用于在注册表中标记该类型。  
  
    -   `defaultIcon`：用于此文件类型的图标。  该图标必须在应用程序清单中作为文件资源添加。  有关更多信息，请参见[如何：将数据文件包括到 ClickOnce 应用程序中](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
     有关 `file` 和 `fileAssociation` 元素的示例，请参见 [\<fileAssociation\> 元素](../deployment/fileassociation-element-clickonce-application.md)。  
  
5.  如果要将多个文件类型与应用程序关联，请添加其他 `fileAssociation` 元素。  请注意，`progid` 特性应互不相同。  
  
6.  完成应用程序清单后，请重新对该清单签名。  您可以使用 Mage.exe 从命令行执行此操作。  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     有关更多信息，请参见[Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)  
  
## 请参阅  
 [\<fileAssociation\> 元素](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)