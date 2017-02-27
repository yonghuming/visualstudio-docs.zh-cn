---
title: "如何：编写可视化工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, 可视化工具"
  - "可视化工具, 编写"
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：编写可视化工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以为任何托管类（除 <xref:System.Object> 或 <xref:System.Array> 之外）的对象编写自定义可视化工具。  
  
> [!NOTE]
>  **存储**应用仅支持标准文本、HTML、XML 和 JSON 可视化工具。  不支持自定义（用户创建的）可视化工具。  
  
 调试器可视化工具的结构由两部分组成：  
  
-   “调试器端”在 Visual Studio 调试器中运行。  调试器端代码创建并显示可视化工具的用户界面。  
  
-   “调试对象端”在 Visual Studio 正在调试的进程（“调试对象”）中运行。  
  
 要可视化的数据对象（如 String 对象）存在于调试对象进程中。  因此，调试对象端必须将数据对象发送到调试器端，然后调试器端可以使用您创建的用户界面进行显示。  
  
 调试器端从一个*“对象提供程序”*接收要可视化的数据对象，该提供程序可实现 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 接口。  调试器端通过*“对象源”*发送数据对象，该数据源派生自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。  对象提供程序还可以将数据发送回对象源，这样您便能够编写可编辑并显示数据的可视化工具。  可以重写此对象提供程序，以便与表达式计算器进行对话，进而与对象源进行对话  
  
 调试对象端和调试器端通过 <xref:System.IO.Stream> 相互通信。  提供了将数据对象序列化为 <xref:System.IO.Stream> 以及将 <xref:System.IO.Stream> 反序列化为数据对象的方法。  
  
 调试对象端代码是使用 DebuggerVisualizer 特性 \(<xref:System.Diagnostics.DebuggerVisualizerAttribute>\) 指定的。  
  
 若要在调试器端创建可视化工具用户界面，必须创建从 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 继承的类，并且重写 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法来显示界面。  
  
 可以使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 通过可视化工具显示 Windows 窗体、对话框和控件。  
  
 对泛型类型的支持是有限的。  只有在一个泛型类型是开放类型时，才可以为属于该泛型类型的目标编写可视化工具。  此限制与使用 `DebuggerTypeProxy` 特性时的限制相同。  有关详细信息，请参阅[使用 DebuggerTypeProxy 特性](../debugger/using-debuggertypeproxy-attribute.md)。  
  
 自定义可视化工具可能有安全性问题。  请参阅[可视化工具安全注意事项](../debugger/visualizer-security-considerations.md)。  
  
 下面的过程高度概括了创建可视化工具时所需完成的操作。  有关更多详细说明，请参见[演练：用 C\# 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)。  
  
### 创建调试器端  
  
1.  使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 方法在调试器端获取可视化的对象。  
  
2.  创建一个从 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 继承的类。  
  
3.  重写 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以显示接口。  使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 方法将 Windows 窗体、对话框和控件显示为界面的一部分。  
  
4.  应用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，为它指定可视化工具 \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\)。  
  
### 创建调试对象端  
  
1.  应用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，为它指定可视化工具 \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\) 和对象源 \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>\)。  如果省略对象源，则使用默认对象源  
  
2.  如果希望可视化工具能够编辑和显示数据对象，则需要重写 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 中的 `TransferData` 或 `CreateReplacementObject` 方法。  
  
## 请参阅  
 [可视化工具](../debugger/create-custom-visualizers-of-data.md)   
 [如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)   
 [如何：测试和调试可视化工具](../Topic/How%20to:%20Test%20and%20Debug%20a%20Visualizer.md)   
 [可视化工具安全注意事项](../debugger/visualizer-security-considerations.md)