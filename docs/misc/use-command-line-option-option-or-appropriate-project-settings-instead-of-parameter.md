---
title: "使用命令行选项“&lt;option&gt;”或适当的项目设置代替“&lt;parameter&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41008"
  - "vbc41008"
helpviewer_keywords: 
  - "BC41008"
ms.assetid: 1c5d6d7a-b767-4dae-aa61-d7fa81d5aad1
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 使用命令行选项“&lt;option&gt;”或适当的项目设置代替“&lt;parameter&gt;”
指定一个包括一个用于程序集的公共密钥、一个用于程序集的公共密钥容器或一个部分签名的程序集的首选方式是，使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 编译器选项。 不建议在代码中使用 <xref:System.Reflection.AssemblyKeyFileAttribute>、<xref:System.Reflection.AssemblyKeyNameAttribute> 或 <xref:System.Reflection.AssemblyDelaySignAttribute> 特性。  
  
 **错误 ID：**BC41008  
  
### 更正此错误  
  
1.  在代码中使用 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)、[\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) 或 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 编译器选项，而不使用 <xref:System.Reflection.AssemblyKeyFileAttribute>、<xref:System.Reflection.AssemblyKeyNameAttribute> 或 <xref:System.Reflection.AssemblyDelaySignAttribute> 特性。  
  
## 请参阅  
 [如何：创建签名的友元程序集](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic 命令行编译器](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)   
 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)   
 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)