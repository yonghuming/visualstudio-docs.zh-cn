---
title: "“选项”对话框 -&gt;“项目”-&gt;“Visual Basic 默认值” | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Option Explicit 语句，在 IDE 中设置"
  - "Option Compare 语句，在 IDE 中设置"
  - "Option Strict 语句，在 IDE 中设置"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “选项”对话框 -&gt;“项目”-&gt;“Visual Basic 默认值”
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

对于 Visual Basic 项目选项指定默认设置。  当新项目时，将创建指定的选项语句将添加到在代码编辑器中项标头。  选项适用于所有 Visual Basic 项目。  
  
 若要访问此对话框，请在 **工具** 菜单上，单击 **选项**，展开 **项目和解决方案** 文件夹，然后单击 **VB 默认值**。  
  
 Option Explicit  
 设置编译器默认值，以便需要显式声明变量。  默认情况下， **Option Explicit** 设置为 **给**。  有关更多信息，请参见 [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)。  
  
 Option Strict  
 设置编译器默认值，以便需要显式收缩转换，并且后期绑定不允许的。  默认情况下， **Option Strict** 设置为 **关闭**。  有关更多信息，请参见 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)。  
  
 Option Compare  
 设置字符串比较的编译器默认:二进制 \(区分大小写\) 或文本 \(不区分大小写。\) 默认情况下， **Option Compare** 设置为 **二进制**。  有关更多信息，请参见 [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)。  
  
 Option Infer  
 设置局部类型推理的编译器默认值。  默认情况下， **Option Infer** 设置为新创建的项目的 **给** 以及在 Visual Basic 的早期版本创建的迁移项目的 **关闭** 。  有关更多信息，请参见 [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)。  
  
## 请参阅  
 [解决方案和项目](../../ide/solutions-and-projects-in-visual-studio.md)