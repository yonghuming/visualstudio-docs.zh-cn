---
title: "如何：使用“寄存器”窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.registers"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "寄存器，调试"
  - "寄存器目录"
  - "标志，“寄存器”窗口"
  - "寄存器组"
  - "调试 [Visual Studio]，“寄存器”窗口"
  - "“寄存器”窗口"
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用“寄存器”窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

只有在**“选项”**对话框中**“调试”**节点下的**“常规”**类别中启用了地址级调试后，“寄存器”窗口才可用。  
  
 **“寄存器”**窗口显示寄存器内容。  如果在逐句通过程序的过程中将**“寄存器”**窗口保持打开状态，则在代码执行时会看到寄存器值的变化。  最近更改过的值显示为红色。  您可以编辑寄存器的值。  有关详细信息，请参阅[如何：编辑寄存器值](../debugger/how-to-edit-a-register-value.md)。  
  
 为了减少混乱，**“寄存器”**窗口将寄存器组织成组，具体情况随平台和处理器类型的不同而不同。  可以根据需要显示或隐藏组。  有关更多信息，请参见[如何：显示和隐藏寄存器组](../debugger/how-to-display-and-hide-register-groups.md)。  
  
 有关寄存器和“寄存器”窗口背后概念的高级别介绍，请参见 [调试基础知识：“寄存器”窗口](../debugger/debugging-basics-registers-window.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 显示“寄存器”窗口  
  
-   在**“调试”**菜单上选择**“窗口”**，再选择**“寄存器”**。  
  
     调试器必须正在运行或处于中断模式。  
  
    > [!NOTE]
    >  寄存器信息对于脚本或 SQL 应用程序不可用。  
  
## 请参阅  
 [调试基础知识：“寄存器”窗口](../debugger/debugging-basics-registers-window.md)   
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)   
 [调试基础知识：“寄存器”窗口](../debugger/debugging-basics-registers-window.md)