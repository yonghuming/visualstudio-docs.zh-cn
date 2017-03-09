---
title: "Invalid assembly strong name or name not specified | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.invalid_strong_name"
ms.assetid: cb02b69d-09a9-478f-914c-fbdc420e973d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Invalid assembly strong name or name not specified
项目系统的对象模型中的项目属性为空白，该属性使您能够为一些项目指定密钥名或密钥容器，这些项目将生成到具有强名称的程序集（签名的程序集）中。  如果显示此信息，则生成将不会成功。  
  
### 更正此错误  
  
1.  确保在代码中指定了密钥容器名称或密钥文件。  
  
## 请参阅  
 [创建和使用具有强名称的程序集](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)