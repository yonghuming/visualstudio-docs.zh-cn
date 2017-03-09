---
title: "MSBuild 错误 MSB3148 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoOutputPath"
helpviewer_keywords: 
  - "MSB3148"
ms.assetid: 389b335f-5760-4dcc-9146-c52d6d7ac81f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3148
**MSB3148: 生成设置中未指定输出路径。**  
  
 此错误会在输出路径为空或无效时发生；例如，如果项目文件中出现 `OutputPath=""`，则发生此错误。  输出路径的默认值为 `CurrentDirectory`。  
  
### 更正此错误  
  
-   确保 `OutputPath` 不为空，或者项目文件中不出现该属性。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)