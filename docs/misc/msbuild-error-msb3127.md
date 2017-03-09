---
title: "MSBuild 错误 MSB3127 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.FileAssociationDefaultIconNotInstalled"
helpviewer_keywords: 
  - "MSB3127"
ms.assetid: 161eea9a-332f-463e-a49e-d4030e937d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3127
**MSB3127: 未能在当前文件引用中找到默认图标 \<图标名\>，或者该图标不是所需下载组的一部分。  默认图标文件名区分大小写，因此应用程序清单中引用的文件名必须与图标的文件名完全匹配。**  
  
 发布配置为使用文件关联的应用程序时，清单中引用的默认图标必须位于当前文件引用中，或者必须是所需下载组的一部分。  默认图标是为具有配置的文件关联（配置的文件扩展名）的文件显示的图标。  
  
### 更正此错误  
  
-   将图标文件添加到当前项目中，并将其包含在所需下载组中。  有关更多信息，请参见[如何：指定通过 ClickOnce 发布的文件](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md)。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)