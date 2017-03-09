---
title: "警告：同一依赖程序集的不同版本之间出现冲突 | Microsoft Docs"
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
  - "ResolveAssemblyReference.SuggestedRedirects"
ms.assetid: fd14a789-bbdf-46c7-bcd3-9d3165adf96d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 警告：同一依赖程序集的不同版本之间出现冲突
会显示此警告，如果您的项目依赖项关系图包含对同一程序集的不同版本。  
  
 如果具有 app.config 文件，则 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可以添加绑定重定向到它。  绑定重定向所有程序集引用重定向到程序集的最高编号版本的强制说明。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 保存在 app.config 的重定向信息。  如果使用绑定重定向，则不会再出现此警告。  
  
 如果您决定不添加绑定重定向，项目将象以前一样继续引用程序集的同一版本。  但是，仍出现此警告。  
  
### 更正此错误  
  
-   双击该警告并选择 “是”，若收到提示， “希望通过添加绑定这些冲突重于 app.config 文件的记录定向?”