---
title: "如何：使用“编辑并继续”在中断模式下应用编辑 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "中断模式, 应用代码更改"
  - "代码, 在中断模式中编辑"
  - "编码, 在中断模式中编辑"
  - "编辑并继续 [Visual Basic], 在中断模式中应用编辑"
  - "编辑并继续, 在中断模式中应用编辑"
  - "编辑, 中断模式"
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# 如何：使用“编辑并继续”在中断模式下应用编辑
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以在中断模式下使用“编辑并继续”编辑代码，然后不必停止和重新启动执行即可继续。  
  
 在以下调试方案中，“编辑并继续”不可用：  
  
-   混合模式（本机\/托管）调试。  
  
-   SQL 调试。  
  
-   调试 Dr.  Watson 转储。  
  
-   在未选择**“在未经处理的异常上展开调用堆栈”**选项的情况下，在发生未经处理的异常之后编辑代码。  
  
-   调试嵌入式运行时应用程序。  
  
-   从**“调试”**菜单中使用**“附加到”**调试应用程序，而不是使用**“启动”**运行应用程序。  
  
-   调试优化后的代码。  
  
-   当目标为 64 位应用程序时，调试托管代码。  如果希望使用“编辑并继续”，必须将目标平台设置为 x86  （*项目***“属性”**对话框 \-\>**“编译”**选项卡 \-\>**“高级编译器”**设置。）  
  
-   如果由于生成错误无法生成新版本的代码，则对旧版本的代码进行调试。  
  
### 在中断模式下编辑代码  
  
1.  执行下列操作之一进入中断模式：  
  
    -   在代码中设置断点，从**“调试”**菜单选择**“开始调试”**，然后等待应用程序命中断点。  
  
         \- 或 \-  
  
    -   开始调试，然后从**“调试”**菜单中选择**“全部中断”**。  
  
         \- 或 \-  
  
    -   当发生异常时，从**“异常助手”**选择**“启用编辑”**。  
  
2.  进行所需的并且合法的代码更改。  
  
     有关详细信息，请参阅[Visual Basic“编辑并继续”中不支持的编辑](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)。  
  
    > [!NOTE]
    >  如果尝试进行“编辑并继续”所不允许的代码更改，你的编辑将被加上紫色波浪线，并且“任务列表”中会出现一项任务。  除非撤消非法的代码更改，否则将无法继续执行代码。  
  
3.  在**“调试”**菜单上，单击**“继续”**，以继续执行。  
  
     在你所做的编辑已并入项目并已应用的情况下，你的代码继续执行。  
  
## 请参阅  
 [Visual Basic“编辑并继续”中不支持的编辑](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [编辑并继续 \(Visual Basic\)](../debugger/edit-and-continue-visual-basic.md)