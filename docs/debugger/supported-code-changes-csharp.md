---
title: "受支持的代码更改 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "编辑并继续 [C#], 受支持的代码更改"
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 受支持的代码更改 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“编辑并继续”处理方法体内的大多数类型的代码更改。  但是，方法体外的大多数更改以及方法体内的小部分更改在调试期间不能应用。  若要应用这些不受支持的更改，您必须停止调试，重新开始新版本的代码。  
  
 在调试会话期间，不能对 C\# 代码应用下列更改：  
  
-   对当前语句或任何其他活动语句的更改。  
  
     活动语句包括为转至当前语句而调用过的任何语句（位于调用堆栈的函数中）。  
  
     当前语句在源窗口中以黄色背景标记。  其他活动语句以阴影背景标记，并且是只读的。  可在**“选项”**对话框中更改这些默认颜色。  
  
-   更改类型的签名。  
  
-   添加匿名方法，该方法捕获之前未被捕获的变量。  
  
-   添加、移除或更改特性。  
  
-   添加、移除或更改 `using` 指令。  
  
-   在活动语句前后添加 `foreach`、`using` 或 `lock`。  
  
## 不安全代码  
 对不安全代码的更改具有与对安全代码的更改相同的限制，但它还包含一条附加限制：“编辑并继续”不支持对包含 `stackalloc` 运算符的方法内退出的不安全代码所作的更改。  
  
## 异常  
 “编辑并继续”支持对 `catch` 和 `finally` 块的更改，除了不允许在活动语句周围添加 `catch` 或`finally` 块以外。  
  
## 不支持的方案  
 在以下调试方案中，“编辑并继续”不可用：  
  
-   在某些情况下调试 LINQ 代码。  有关详细信息，请参阅[调试 LINQ](../debugger/debugging-linq.md)。  
  
    -   捕获之前尚未捕获的变量。  
  
    -   更改查询表达式的类型（例如，select a \=\> select new { A \= a };）  
  
    -   删除包含活动语句的 `where`。  
  
    -   删除包含活动语句的 `let`。  
  
    -   删除包含活动语句的 `join`。  
  
    -   删除包含活动语句的 `orderby`。  
  
-   混合模式（本机\/托管）调试。  
  
-   SQL 调试。  
  
-   调试 Dr.  Watson 转储。  
  
-   在未选择**“在未经处理的异常上展开调用堆栈”**选项的情况下，在发生未经处理的异常之后编辑代码。  
  
-   调试嵌入式运行时应用程序。  
  
-   调试具有**“附加到”**的应用程序，而不是通过选择**“调试”**菜单上的**“启动”**来运行应用程序。  
  
-   调试优化后的代码。  
  
-   如果由于生成错误无法生成新版本的代码，则对旧版本的代码进行调试。  
  
## 请参阅  
 [编辑并继续 \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [如何：使用“编辑并继续”\(C\#\)](../debugger/how-to-use-edit-and-continue-csharp.md)