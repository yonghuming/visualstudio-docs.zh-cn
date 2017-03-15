---
title: "Unable to remove the last generated output | Microsoft Docs"
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
  - "vs.tasklisterror.remove_last_genoutput_failure"
ms.assetid: 329a5e56-9b1f-4e41-8b0f-4bd64b8311d0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to remove the last generated output
未将已知的最后生成的输出从磁盘和\/或项目中移除。  
  
 如果自定义工具返回失败，则将从磁盘和该项目中移除最后生成的输出（如果有的话）。  
  
 如果生成的输出被锁定在磁盘上，则可能发生这种情况。  
  
 **更正此错误**  
  
-   关闭并重新启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。