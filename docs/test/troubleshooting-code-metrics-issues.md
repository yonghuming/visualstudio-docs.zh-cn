---
title: "代码度量值问题疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
caps.handback.revision: 4
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# 代码度量值问题疑难解答
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

收集代码度量值时，可能会遇到以下一些问题：  
  
-   [Visual Studio 2010 中的代码复杂性计算更改](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Visual Studio 2010 中的代码复杂性计算更改  
 在以下情况下，对于同一函数，[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中计算的代码复杂性度量值可能与 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 早期版本计算的度量值不同：  
  
-   该函数包含一个或多个 catch 块。  在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 的早期版本中，计算中不包含 catch 块。  在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中，将向该函数的复杂性中添加每个 catch 块的复杂性。  
  
-   该函数包含 switch（在 VB 中为 Select Case）语句。  对于一些包含贯穿的 case 的 switch 语句，[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 与早期版本之间的编译器差异可能会生成不同的 MSIL 代码。  
  
## 请参阅  
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)