---
title: "如何：使用“编辑并继续”(C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "编辑并继续 [C#], 关于“编辑并继续”"
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：使用“编辑并继续”(C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 C\# 的“编辑并继续”，可以一边进行调试一边在中断模式下更改代码。  不必停止并重新启动调试会话即可应用更改。  
  
 在中断模式下进行更改时，将自动调用“编辑并继续”，然后选择调试器执行命令（如**“继续”**、**“单步执行”**或**“设置下一语句”**），或在调试器窗口中计算函数。  
  
> [!NOTE]
>  在调试Compact Framework、优化代码、本机\/托管混合代码或 SQL Server 公共语言运行时 \(CLR\) 集成代码时不支持“编辑并继续”。  如果尝试在以上任何一种情况下应用代码更改，则调试器将显示一个对话框，其中说明不支持“编辑并继续”。  
  
### 自动调用“编辑并继续”  
  
1.  在中断模式下，对源代码进行修改。  
  
2.  在**“调试”**菜单中，单击**“继续”**、**“单步执行”**或**“设置下一语句”**，或在调试器窗口中计算函数。  
  
     这会编译新代码并继续调试新的代码。  有些更改不受“编辑并继续”支持。  有关详细信息，请参阅[受支持的代码更改 \(C\#\)](../debugger/supported-code-changes-csharp.md)。  
  
### 启用\/禁用“编辑并继续”  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  在**“选项”**对话框中展开**“调试”**节点，然后选择**“编辑并继续”**。  
  
3.  在**“选项”**的**“编辑并继续”**页中，选择或清除**“启用‘编辑并继续’”**复选框。  
  
     该设置将在重新启动调试会话时生效。  
  
## 请参阅  
 [编辑并继续 \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [受支持的代码更改 \(C\#\)](../debugger/supported-code-changes-csharp.md)   
 [“编辑并继续”错误和警告 \(C\#\)](../misc/edit-and-continue-errors-and-warnings-csharp.md)