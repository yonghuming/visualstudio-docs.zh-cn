---
title: "编译器警告（等级 2）CS1927 | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 2）CS1927
对模块忽略 \/win32manifest，因为它仅应用于程序集。  
  
 win32 清单仅应用于程序集级别。 模块将进行编译，但不具有清单。  
  
### 更正此错误  
  
1.  删除 **\/win32manifest option**。  
  
2.  将代码编译为程序集。  
  
## 示例  
 下面的示例在同时用 **\/target:module** 和 **\/win32manifest** 编译器选项进行编译时生成 CS1927。  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## 请参阅  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](/dotnet/csharp/language-reference/compiler-options/win32manifest-compiler-option)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)