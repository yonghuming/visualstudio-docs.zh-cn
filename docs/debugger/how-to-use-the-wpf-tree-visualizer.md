---
title: "如何：使用 WPF 树可视化工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "调试, WPF"
  - "WPF, 调试"
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用 WPF 树可视化工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用 WPF 树可视化工具浏览 WPF 对象的可视化树，并查看该树中所含对象的 WPF 依赖项属性。  有关可视化树的更多信息，请参见 [WPF 中的树](../Topic/Trees%20in%20WPF.md)。  有关依赖项属性的更多信息，请参见[依赖项属性概述](../Topic/Dependency%20Properties%20Overview.md)。  
  
 当您打开 WPF 树可视化工具后，将看到以下两个窗格：位于左侧的**“可视化树”**窗格和位于右侧的“*Name***:***Type* **属性”**窗格。  选择**“可视化树”**窗格中的任何对象，“*Name***:***Type* **属性”**窗格将自动更新为显示该对象的属性。  
  
### 打开 WPF 树可视化工具  
  
1.  在数据提示、**“监视”**窗口、**“自动”**窗口或**“局部变量”**窗口中，在 WPF 对象名称旁单击放大镜图标旁的箭头。  
  
     将会显示可视化工具列表。  
  
2.  单击**“WPF 树可视化工具”**。  
  
### 搜索可视化树  
  
-   在**“可视化树”**窗格中，在**“搜索”**框中键入要搜索的字符串。  
  
     WPF 树可视化工具将立即在可视化树中查找与您键入的字符串匹配的第一个对象。  键入更多字符可找到更精确的匹配项。  
  
    -   若要转到可视化树中的下一个匹配项，请单击**“下一个”**。  
  
    -   若要返回上一个匹配项，请单击**“上一个”**。  
  
    -   若要清除搜索条件，请单击**“清除”**。  
  
### 搜索属性列表  
  
-   在“*Name***:***Type* **属性”**窗格中，在**“筛选”**框中键入要搜索的字符串。  
  
     WPF 树可视化工具将立即查找与您键入的字符串匹配的属性；现在，列表中仅显示与键入的字符串匹配的那些属性。  键入更多字符可找到更精确的匹配项。  
  
    -   若要清除搜索条件，请单击**“清除”**。  
  
### 关闭可视化工具  
  
-   单击对话框右上角的**“关闭”**图标。  
  
## 请参阅  
 [如何：使用可视化工具](../Topic/How%20to:%20Use%20a%20Visualizer.md)   
 [可视化工具](../debugger/create-custom-visualizers-of-data.md)   
 [WPF 中的树](../Topic/Trees%20in%20WPF.md)   
 [依赖项属性概述](../Topic/Dependency%20Properties%20Overview.md)