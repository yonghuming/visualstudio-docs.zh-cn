---
title: "如何：在混合模式下调试 | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "调试 [Visual Studio], 混合模式"
  - "调试 DLL"
  - "混合模式调试"
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：在混合模式下调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以下过程描述如何调试托管代码和本机代码，这一过程也称作混合模式调试。  根据 DLL 或应用程序是否用本机代码编写，有两种方案可以用来进行调试：  
  
-   调用 DLL 的调用应用程序是用本机代码编写的。  在这种情况下 DLL 是托管的，托管调试器和本机调试器都必须启用，以调试托管代码和本机代码。  可以在**“\<Project\> 属性页”**对话框中选中此选项。  具体如何检查取决于是从 DLL 项目中启动调试，还是从调用应用程序项目中启动调试。  
  
-   调用 DLL 的调用应用程序是用托管代码编写的，而 DLL 是用本机代码编写的。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 启用混合模式调试  
  
1.  在**“解决方案资源管理器”**中，选择项目。  
  
2.  在**“视图”**菜单上，单击**“属性页”**。  
  
3.  在**“\<Project\> 属性页”**对话框中，展开**“配置属性”**节点，然后选择**“调试”**。  
  
4.  将**“调试器类型”**设置为**“混合”**或**“自动”**。  
  
## 请参阅  
 [如何：从 DLL 项目进行调试](../debugger/how-to-debug-from-a-dll-project.md)