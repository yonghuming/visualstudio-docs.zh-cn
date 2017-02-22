---
title: "“列出反汇编”命令 | Microsoft Docs"
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
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly 命令"
  - "“列出反汇编”命令"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “列出反汇编”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

开始调试进程，并允许您指定如何处理错误。  
  
## 语法  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## 开关  
 可以使用开关的完整形式或缩写形式调用每个开关。  
  
 \/count: `number` \[或\] \/c: `number` \[或\] \/length: `number` \[或\] \/l: `number`  
 可选。  要显示的指令的数量。  默认值为 8。  
  
 \/endaddress: `expression` \[或\] \/e: `expression`  
 可选。  停止反汇编的地址。  
  
 \/codebytes:`yes`&#124;`no` \[或\] \/bytes:`yes`&#124;`no` \[或\] \/b:`yes`&#124;`no`  
 可选。  指示是否显示代码字节。  默认值为 `no`。  
  
 \/source:`yes`&#124;`no` \[或\] \/s:`yes`&#124;`no`  
 可选。  指示是否显示源代码。  默认值为 `no`。  
  
 \/symbolnames:`yes`&#124;`no` \[或\] \/names:`yes`&#124;`no` \[或\] \/n:`yes`&#124;`no`  
 可选。  指示是否显示符号名称。  默认值为 `yes`。  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 可选。  可用于查看与源代码关联的行号。  \/source 开关的值必须为 `yes`，才能使用 \/linenumbers 开关。  
  
## 示例  
  
```  
>Debug.ListDisassembly  
```  
  
## 请参阅  
 [“列出调用堆栈”命令](../../ide/reference/list-call-stack-command.md)   
 [“列出线程”命令](../../ide/reference/list-threads-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)