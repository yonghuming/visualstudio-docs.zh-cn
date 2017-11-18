---
title: "创建的数据的自定义可视化工具 |Microsoft 文档"
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec31ea837c78fc1d47c3df02d129ac3c5f4f3657
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-visualizers-of-data"></a>创建数据的自定义可视化的工具
 可视化工具是组件[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]调试器用户界面。 A*可视化工具*创建对话框或另一个接口，以适合于其数据类型的方式显示变量或对象。 例如，HTML 可视化工具解释 HTML 字符串，并按照该字符串出现在浏览器窗口中时的样子显示结果；位图可视化工具解释位图结构并显示该位图结构表示的图形。 某些可视化工具允许您修改数据，还允许您查看数据。

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 调试器包括六个标准可视化工具。 它们分别是文本、 HTML、 XML 和 JSON 可视化工具，它们都在字符串对象; 工作WPF 树可视化工具，用于显示 WPF 对象可视化树; 的属性和数据集可视化工具，一种用于 DataSet、 DataView 和 DataTable 对象。 将来可以从 Microsoft Corporation 以及第三方和社区下载更多的可视化工具。 此外，你可以编写自己的可视化工具，并将它们安装在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 调试器中。

 > [!NOTE]
 > 若要创建本机代码的自定义可视化工具，请参阅[SQLite 本机调试器可视化工具](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer)示例。 在 UWP 和 Windows 8.x 应用中，不支持自定义可视化工具。

 在调试器中，可视化工具由放大镜图标表示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "可视化工具图标")。 当你看到中的放大镜图标**数据提示**，在调试器窗口等**监视**窗口中，或在**快速监视**对话框中，你可以单击到放大镜选择适合于相应对象的数据类型的可视化工具。

## <a name="overview-of-custom-visualizers"></a>自定义可视化工具的概述

可以为任何托管类（除 <xref:System.Object> 或 <xref:System.Array> 之外）的对象编写自定义可视化工具。  
  
 调试器可视化工具的结构由两部分组成：  
  
-   *调试器端*运行在 Visual Studio 调试器中。 调试器端代码创建并显示可视化工具的用户界面。  
  
-   *调试对象端*程序在 Visual Studio 正在调试的进程中运行 (*调试对象*)。  
  
 要可视化的数据对象（如 String 对象）存在于调试对象进程中。 因此，调试器端必须将数据对象发送到调试对象端，然后调试器端可以使用您创建的用户界面进行显示。  
  
 调试器端接收要从可视化此数据对象*对象提供程序*实现<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>接口。 调试对象端发送数据对象，通过*对象源*，该类派生自<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。 对象提供程序还可以将数据发送回对象源，这样您便能够编写可编辑并显示数据的可视化工具。 可以重写此对象提供程序，以便与表达式计算器进行对话，进而与对象源进行对话  
  
 调试对象端和调试器端通过 <xref:System.IO.Stream> 相互通信。 提供了将数据对象序列化为 <xref:System.IO.Stream> 以及将 <xref:System.IO.Stream> 反序列化为数据对象的方法。  
  
 调试对象端代码是使用 DebuggerVisualizer 特性 (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) 指定的。  
  
 若要在调试器端创建可视化工具用户界面，必须创建从 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 继承的类，并且重写 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法来显示界面。  
  
 可以使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 通过可视化工具显示 Windows 窗体、对话框和控件。  
  
 对泛型类型的支持是有限的。 只有在一个泛型类型是开放类型时，才可以为属于该泛型类型的目标编写可视化工具。 此限制与使用 `DebuggerTypeProxy` 特性时的限制相同。 有关详细信息，请参阅[使用 DebuggerTypeProxy 特性](../debugger/using-debuggertypeproxy-attribute.md)。  
  
 自定义可视化工具可能有安全性问题。 请参阅[可视化工具安全注意事项](../debugger/visualizer-security-considerations.md)。  
  
 下面的过程高度概括了创建可视化工具时所需完成的操作。 有关更多详细说明，请参阅[演练： 在 C# 中编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)。  
  
### <a name="to-create-the-debugger-side"></a>创建调试器端  
  
1.  使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 方法在调试器端获取可视化的对象。  
  
2.  创建一个从 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 继承的类。  
  
3.  重写 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以显示接口。 使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 方法将 Windows 窗体、对话框和控件显示为界面的一部分。  
  
4.  应用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，为它指定可视化工具 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)。  
  
### <a name="to-create-the-debuggee-side"></a>创建调试对象端  
  
1.  应用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，为它指定可视化工具 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) 和对象源 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)。 如果省略对象源，则使用默认对象源  
  
2.  如果希望可视化工具能够编辑和显示数据对象，则需要重写 `TransferData` 中的 `CreateReplacementObject` 或 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 方法。   
  
## <a name="in-this-section"></a>本节内容
  
 [演练：用 C# 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [演练：用 Visual Basic 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：测试和调试可视化工具](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [可视化工具 API 参考](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>相关章节  
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)