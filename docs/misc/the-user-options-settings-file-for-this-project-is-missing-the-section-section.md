---
title: "The user options settings file for this project is missing the &#39;section&#39; section | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.peruserfile_sectionerr"
ms.assetid: 576070f5-76b6-46e4-8aba-83442521027f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The user options settings file for this project is missing the &#39;section&#39; section
.vbproj.user 或 .csproj.user 文件缺少 Build 节点。  
  
 Build 节包含调试设置。  如果缺少该节，将不加载调试设置，而使用默认值。  
  
 此错误很可能由手动编辑项目文件引起。  
  
 当关闭项目时，项目系统将自动重写每个用户的项目文件。  
  
 这是一种信息性警告。  
  
## 请参阅  
 [项目文件](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)