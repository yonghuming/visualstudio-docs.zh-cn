---
title: "MSBuild 错误 MSB3180 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3180
**“MSB3180：在‘\<文件\>’和‘\<文件\>’中都定义了 COM 组件‘\<程序集\>’，clsid\/tlbid\=‘\<程序集\>’。”**  
  
 当在文件引用或依赖清单中找到对类或类型库的重复 COM 引用时，应用程序清单生成过程将产生此错误。  
  
 例如，如果将引用添加到带有外部清单的 COM 对象中，以及将引用添加到带有内部清单的同一 COM 对象中，就可能会收到此错误。  
  
### 更正此错误  
  
-   移除重复 COM 引用中的某一个。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)