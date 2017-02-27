---
title: "可视化工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.visualizer.troubleshoot"
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
  - "调试器, 可视化工具"
  - "可视化工具"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# 可视化工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可视化工具是 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 调试器用户界面的组件。  “可视化工具”可用来创建对话框或其他界面，以一种适合于变量或对象数据类型的方式来显示变量或对象。  例如，HTML 可视化工具解释 HTML 字符串，并按照该字符串出现在浏览器窗口中时的样子显示结果；位图可视化工具解释位图结构并显示该位图结构表示的图形。  某些可视化工具允许您修改数据，还允许您查看数据。  
  
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 调试器包括六个标准可视化工具。  它们分别是文本可视化工具、HTML 可视化工具、XML 可视化工具 和 JSON 可视化工具、WPF 树可视化工具以及数据集可视化工具，前四种均用于字符串对象，第五种用于显示 WPF 对象可视化树的属性，最后一种用于 DataSet、DataView 和 DataTable 对象。  将来可以从 Microsoft Corporation 以及第三方和社区下载更多的可视化工具。  此外，你可以编写自己的可视化工具，并将它们安装在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 调试器中。  
  
> [!NOTE]
>  **存储**应用仅支持标准文本、HTML、XML 和 JSON 可视化工具。  不支持自定义（用户创建的）可视化工具。  
  
 可视化工具在调试器中用放大镜图标表示。  当您在**“数据提示”**、调试器变量窗口或**“快速监视”**对话框中看到放大镜图标时，可单击该放大镜以选择适合于相应对象的数据类型的可视化工具。  
  
 Compact Framework 上不支持可视化工具。  
  
> [!NOTE]
>  调试器可视化工具要求比部分信任的应用程序允许的特权更大的特权。  因此，在部分信任的代码中停止时，可视化工具不会加载。  若要使用可视化工具进行调试，必须运行完全信任的代码。  
  
## 本节内容  
 [如何：编写可视化工具](../debugger/how-to-write-a-visualizer.md)  
  
 [演练：用 C\# 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：测试和调试可视化工具](../Topic/How%20to:%20Test%20and%20Debug%20a%20Visualizer.md)  
  
 [可视化工具 API 参考](../debugger/visualizer-api-reference.md)  
  
## 相关章节  
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)