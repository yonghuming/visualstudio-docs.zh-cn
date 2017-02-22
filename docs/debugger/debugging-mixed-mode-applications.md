---
title: "调试混合模式应用程序 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "“调用堆栈”窗口"
  - "“调用堆栈”窗口, 混合模式调试"
  - "调试 [Visual Studio], 混合模式"
  - "调试托管代码, 混合模式"
  - "混合模式调试"
  - "混合模式调试, 调用堆栈"
  - "混合模式调试, 属性计算"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 调试混合模式应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

混合模式应用程序是任何组合了本机代码 \(C\+\+\) 与托管代码（在公共语言运行时上运行的 Visual Basic、Visual C\# 或 C\+\+）的应用程序。  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中调试混合模式应用程序基本上是透明的；它与调试单模式应用程序没有太大区别。  但有几个特殊的注意事项。  
  
## 在混合模式调试下启用 C\+\+“编辑并继续”  
  
-   若要使用 Visual Studio 2013 中的 C\+\+“编辑并继续”功能，你必须还原为旧调试引擎。  请参阅“Microsoft 应用程序生命周期管理”博客上的[切换为 Visual Studio 2013 中的托管兼容性模式](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx)。  
  
## 混合模式应用程序中的属性求值  
 在混合模式应用程序中，调试器执行的属性求值是一个资源消耗很大的操作。  因此，调试操作（如单步执行）可能会很慢。  有关详细信息，请参阅[单步执行](http://msdn.microsoft.com/zh-cn/8791dac9-64d1-4bb9-b59e-8d59af1833f9)。  如果混合模式调试的性能很低，你可能希望在调试器窗口中关闭属性求值。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
#### 关闭属性求值  
  
1.  在**“工具”**菜单上，选择**“选项”**。  
  
2.  在**“选项”**对话框中，打开**“调试”**文件夹并选择**“常规”**类别。  
  
3.  清除**“启用属性求值和其他隐式函数调用”**复选框。  
  
 由于本机调用堆栈和托管调用堆栈不同，因此调试器不能总是为混合代码提供完整的调用堆栈。  当本机代码调用托管代码时，你可能会注意到某些差异。  有关详细信息，请参阅[“调用堆栈”窗口中的混合代码与丢失信息](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)。  
  
## 请参阅  
 [调试托管代码](../debugger/debugging-managed-code.md)