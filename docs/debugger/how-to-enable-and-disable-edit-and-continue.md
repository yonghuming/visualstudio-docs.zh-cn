---
title: "如何：启用和禁用“编辑并继续” | Microsoft Docs"
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
  - "/INCREMENTAL 链接器选项"
  - "“应用代码更改”命令"
  - "中断模式, 应用代码更改"
  - "代码更改, 在中断模式中应用"
  - "编辑并继续, 应用代码更改"
  - "编辑并继续, 禁用"
  - "编辑并继续, 启用"
  - "“进行”命令"
  - "INCREMENTAL 链接器选项"
  - "“单步执行”命令"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：启用和禁用“编辑并继续”
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

设计时，可以在**“选项”**对话框中禁用或启用“编辑并继续”。  无法在调试过程中更改此设置。  
  
 “编辑并继续”仅在调试版本中起作用。  对于本机 C\+\+，“编辑并继续”需要使用 \/INCREMENTAL 选项。  
  
## 过程  
  
#### 启用\/禁用“编辑并继续”  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  在**“选项”**对话框中，打开**“调试”**节点，然后选择**“编辑并继续”**类别。  
  
3.  若要启用它，请选中**“启用‘编辑并继续’”**复选框。  若要禁用它，请清除该复选框。  
  
    > [!NOTE]
    >  如果启用了 IntelliTrace 并且收集 IntelliTrace 事件和调用信息，则会禁用“编辑并继续”。  有关详细信息，请参阅[配置 IntelliTrace 以收集调试信息](http://msdn.microsoft.com/zh-cn/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
4.  单击**“确定”**。  
  
## 请参阅  
 [编辑并继续](../debugger/edit-and-continue.md)   
 [“选项”对话框 \-\>“调试”\-\>“编辑并继续”](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)