---
title: "MSBuild 错误 MSB3184 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3184
**MSB3184：输入清单无效。**  
  
 当生成过程尝试加载一个文件并预期该文件包含应用程序清单或部署清单，但结果该文件包含其他内容（如不同的清单或损坏的数据）时，将产生此错误。  
  
### 更正此错误  
  
-   验证项目中的清单是否有效和适当。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)