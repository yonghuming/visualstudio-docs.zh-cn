---
title: "“陈旧代码警告”对话框 | Microsoft Docs"
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
  - "vs.debug.ENC.stalecode"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "“陈旧代码警告”对话框"
  - "代码，陈旧代码警告"
  - "警告，“陈旧代码警告”对话框"
  - "编辑并继续，陈旧代码"
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “陈旧代码警告”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当**“编辑并继续”**操作未能立即应用对本机代码所做的更改时，将显示此对话框。  因此，当前堆栈帧中的某些本机代码是过时的、陈旧的。  有关详细信息，请参阅[How to: Work with Stale Code](http://msdn.microsoft.com/zh-cn/c7536e95-66a6-44a0-995d-3fe5035250b4)。  
  
 **不再显示此对话框**  
 如果选中此复选框，则“编辑并继续”以后将在不要求权限的情况下应用代码更改。  可以通过转到**“选项”**对话框，打开**“调试”**文件夹，单击**“编辑并继续”**页，然后选择**“就陈旧的代码发出警告”**来再次启用此警告。  
  
## 请参阅  
 [受支持的代码更改和限制 \(C\+\+\)](../debugger/supported-code-changes-cpp.md)   
 [“选项”对话框 \-\>“调试”\-\>“编辑并继续”](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)