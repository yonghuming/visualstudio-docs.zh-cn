---
title: "如何：使用工作流设计器调试 XAML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 如何：使用工作流设计器调试 XAML
工作流是以 XAML 的形式定义的。工作流的 UI 表示形式建立在定义该工作流的 XAML 树之上。该调试体验与在 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中调试工作流类似。例如，调试 XAML 时，“局部变量”、“监视”和“线程”窗口与它们在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 调试中的工作方式相同。此外，在 XAML 调试过程中，“调用堆栈”视图是工作流执行流的基于行的分层视图。  
  
> [!NOTE]
>  如果为工作流的 XAML 位于同一程序集作为活动中，程序集部分不包括在类名称内。没有这类（活动）名称的一部分，不能在运行时加载 XAML。不建议在同一命名空间作为主项目中定义的活动；否则，XAML 会需要手工编辑后正在编辑在设计器中。  
  
### 调试工作流 XAML  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中打开工作流或活动项目。  
  
2.  对要调试的一个或多个活动设置断点，如[如何：在工作流中设置断点](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)中所述。  
  
3.  右击包含工作流定义的 .xaml 文件，然后选择**“查看代码”**。您将看到在设计视图中对其设置了断点的活动的 XAML 元素声明所在行中显示了一个断点。  
  
4.  调用调试器，如[如何：调用工作流调试器](../workflow-designer/how-to-invoke-the-workflow-debugger.md) 中所述。  
  
5.  当代码执行到您设置的其中一个断点处时，与该断点关联的 XAML 元素将突出显示。若要移到下一个断点，请使用 **F10** 或 **F11** 键。  
  
## 请参阅  
 [如何：在工作流中设置断点](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [如何：调用工作流调试器](../workflow-designer/how-to-invoke-the-workflow-debugger.md)