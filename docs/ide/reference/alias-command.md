---
title: "“别名”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.alias"
helpviewer_keywords: 
  - "“别名”命令"
  - "别名, Visual Studio 命令"
  - "命令别名"
  - "命令, 别名"
  - "Tools.Alias 命令"
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “别名”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

为完整命令、完整命令和参数或另一个别名创建新别名。  
  
> [!TIP]
>  键入不带任何参数的 `>alias` 会显示当前别名及其定义的列表。  
  
## 语法  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## 实参  
 `aliasname`  
 可选。  新别名的名称。  如果没有为 `aliasname` 提供值，则出现当前别名及其定义的列表。  
  
 `aliasstring`  
 可选。  要为其创建别名的完整命令名或现有别名以及任何参数。  如果没有为 `aliasstring` 提供值，则显示指定别名的别名和别名字符串。  
  
## 开关  
 \/delete 或 \/del 或 \/d  
 可选。  删除指定别名，将其从自动完成中移除。  
  
 \/reset  
 可选。  把预定义别名列表重置为其原始设置，  即，还原所有预定义别名并移除所有用户定义的别名。  
  
## 备注  
 因为别名表示命令，它们必须位于命令行的开始处。  
  
 发出此命令时，应紧跟在命令（而不是别名）后加上开关，否则开关本身也将成为别名字符串的一部分。  
  
 `/reset` 开关会在还原别名前请求确认。  `/reset` 没有缩写形式。  
  
## 示例  
 此示例将为完整的命令 Edit.MakeUpperCase 创建一个新的别名：`upper`。  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 此示例将删除别名：`upper`。  
  
```  
>Tools.alias /delete upper  
```  
  
 此示例显示所有当前别名及其定义的列表。  
  
```  
>Tools.Alias  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)