---
title: "“编辑并继续”错误消息对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.SupportedButNotAvaiable"
  - "vs.debug.ENC.CannotEditWhileException"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "“编辑并继续”错误消息对话框"
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# “编辑并继续”错误消息对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在使用支持“编辑并继续”的语言进行调试时，此对话框会出现，但**“编辑并继续”**不能用于所做的代码更改的类型。  此框中的错误消息提供了更加详细的说明。  此对话框出现的可能原因包括：  
  
-   尝试在启用非托管调试时编辑托管代码。  “编辑并继续”不可用于混合模式调试。  
  
-   尝试编辑 SQL Server 代码。  
  
-   尝试在调试 Dr. Watson 转储期间编辑  代码。  
  
-   尝试在发生未经处理的异常且未选择**“在未经处理的异常上展开调用堆栈”**选项时编辑代码。  
  
-   尝试在调试嵌入的运行时应用程序时编辑代码。  
  
-   尝试在附加到（而不是从**“调试”**菜单启动）的程序中编辑代码。  
  
-   尝试编辑优化的代码。  
  
-   尝试在目标为 64 位应用程序时编辑托管代码。  如果希望使用“编辑并继续”，必须将目标平台设置为 x86（“*Project* **属性”**、**“编译”**选项卡、**“高级编译器”**设置。）。  
  
-   尝试编辑在调试过程中修改过并已重新加载的程序集中的代码。  
  
-   尝试编辑尚未加载的程序集中的代码。  
  
-   开始调试旧版本的应用程序（由于新版本具有生成错误）。  
  
-   尝试在代码运行时编辑代码。  
  
## UIElement 列表  
 **确定**  
 退出对话框并取消之前的编辑尝试。  
  
## 请参阅  
 [受支持的代码更改和限制 \(C\+\+\)](../debugger/supported-code-changes-cpp.md)