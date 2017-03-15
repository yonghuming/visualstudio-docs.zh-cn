---
title: "MSBuild 错误 MSB3154 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
helpviewer_keywords: 
  - "MSB3154"
ms.assetid: 513b70fa-15f5-4137-bdbc-5974607fb75a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3154
**MSB3154: 未能找到项“\<package\>”的字符串资源。**  
  
 此错误会在指定的程序包不包含任何区域性特定的信息时产生。  或者 package.xml 文件不存在，或者该文件不包含 `Culture` 特性。  
  
### 更正此错误  
  
-   提供一个含有正确 `Culture` 标记的有效 package.xml。