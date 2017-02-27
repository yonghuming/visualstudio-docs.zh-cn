---
title: "Visual Basic 特定的 IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [Visual Basic]"
  - "IntelliSense [Visual Studio], Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Visual Basic 特定的 IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Basic 源代码编辑器提供了以下 Intellisense 功能：  
  
-   语法提示  
  
     语法提示显示正在键入的语句的语法。  这对于诸如 [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) 等语句很有用。  
  
## 自动完成  
  
-   完成各种关键字  
  
     例如，如果键入 `goto` 和一个空格，Intellisense 将在一个下拉菜单中显示已定义标签的列表。  所支持的其他关键字包括 `Exit`、`Implements`、`Option` 和 `Declare`。  
  
-   完成 `Enum` 和 `Boolean`  
  
     当一条语句将引用枚举成员时，IntelliSense 将显示 `Enum` 的成员列表。  当一条语句将引用某个 `Boolean` 时，Intellisense 将显示一个“真\/假”下拉菜单。  
  
 通过从**“Visual Basic”**文件夹的**“常规”**属性页中取消选择**“自动列出成员”**，可以默认关闭完成功能。  
  
 您可以通过调用列表成员、 完成单词或 ALT \+ 向右键手动调用完成。  有关更多信息，请参见[使用 IntelliSense](../ide/using-intellisense.md)。  
  
## 区域 IntelliSense  
 “区域 IntelliSense”可以帮助那些需要通过 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署应用程序并受部分信任设置约束的 Visual Basic 开发人员。  此功能：  
  
-   使您能够选择运行该应用程序所使用权限。  
  
-   将所选区域中的 API 在“列出成员”中显示为可用，将需要额外权限的 API 显示为不可用。  
  
 有关更多信息，请参见 [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)。  
  
## 请参阅  
 [使用 IntelliSense](../ide/using-intellisense.md)