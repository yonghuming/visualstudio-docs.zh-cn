---
title: "MSBuild 错误 MSB3187 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3187
**MSB3187：引用程序集“'\<\<assembly\>\>”面向的是另一个处理器，而不是应用程序。**  
  
 当应用程序的目标平台（处理器结构）设置为非特定的 \(MSIL\) 而引用的程序集为特定的，或者如果应用程序的结构是特定的，而依赖项为非特定的时，将产生此警告。  而且，如果以上二者均为特定于平台的，则它们的结构必须相互匹配。  此外，应用程序结构与入口点程序集结构必须始终匹配。  
  
### 更正此错误  
  
-   确保应用程序的目标平台（处理器结构）与所有引用的程序集和入口点程序集结构相匹配。  
  
## 请参阅  
 [“高级编译器设置”对话框 \(Visual Basic\)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)   
 [“项目设计器”\-\>“生成”页 \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)