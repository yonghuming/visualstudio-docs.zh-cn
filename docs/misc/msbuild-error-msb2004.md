---
title: "MSBuild 错误 MSB2004 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MultipleLanguageNodesNotAllowed"
helpviewer_keywords: 
  - "MSB2004"
ms.assetid: ae426d42-7a97-44b6-b0df-12fdef7d0ee7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB2004
**元素 \<{0}\> 不能包含多个语言节点。**  
  
 一个项目文件只能包含一个语言节点。  
  
### 更正此错误  
  
-   检查项目文件是否已被修改或损坏。  如果项目已被修改或损坏，请用创建项目所用的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本将项目打开，保存项目，然后尝试再次转换项目。  
  
## 请参阅  
 [Devenv 命令行开关](../ide/reference/devenv-command-line-switches.md)