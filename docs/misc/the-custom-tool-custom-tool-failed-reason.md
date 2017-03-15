---
title: "The custom tool &#39;custom tool&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.generator_fail_errorinfo"
ms.assetid: e846b946-a123-49fe-b4bc-a7bbda501417
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The custom tool &#39;custom tool&#39; failed. &lt;reason&gt;
自定义工具未成功运行。  
  
 如果您在更新包含 N 层数据集的项目时遇到 MSDataSetGenerator 错误，则在更新所有项目后必须重新运行自定义工具。  
  
 自定义工具“MSDataSetGenerator”失败。  在 \<数据集名称\> 的 DataSetProject 特性中指定的项目必须以等于或晚于当前项目的 .NET Framework 版本为目标。  
  
### 更正 N 层数据集中的 MSDataSetGenerator 错误  
  
-   在解决方案资源管理器中，右击 .xsd 文件，然后单击**“运行自定义工具”**。