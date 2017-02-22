---
title: "如何：设置调试和发布配置 | Microsoft Docs"
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
  - "vs.debug.builds"
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
  - "生成配置, 调试"
  - "生成配置, 发布"
  - "配置, 发布"
  - "调试版本"
  - "调试版本, 更改配置设置"
  - "调试版本, 切换到发行版本"
  - "调试配置"
  - "调试 [Visual Studio], 调试配置"
  - "调试 [Visual Studio], 发行配置"
  - "项目 [Visual Studio], 调试配置"
  - "项目 [Visual Studio], 发行配置"
  - "发行版本, 更改设置"
  - "发行版本, 切换到调试版本"
  - "Visual Basic 项目, 调试和发行版本"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：设置调试和发布配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 项目具有针对你的程序的单独发布和调试配置。  顾名思义，生成调试版本的目的是用于调试，而生成发布版本的目的是用于最终发布分发。  
  
 程序的调试配置使用完整符号调试信息编译，且不进行优化。  优化会使调试复杂化，因为源代码和生成的指令之间的关系更加复杂。  
  
 程序的发布配置进行了完全优化，且不包含任何符号调试信息。  根据使用的编译器选项，可在 PDB 文件中生成调试信息。  如果以后还必须调试发行版本，创建 PDB 文件就非常有用。  
  
 有关生成配置的详细信息，请参阅[了解生成配置](../ide/understanding-build-configurations.md)。  
  
 可以从**“生成”**菜单、从工具栏或在项目的属性页中更改生成配置。  项目属性页是特定于语言的。  下面的过程演示如何从菜单和工具栏更改生成配置。  有关如何在使用不同语言的项目中更改生成配置的详细信息，请参阅下面的“相关主题”一节。  
  
### 更改生成配置  
  
1.  从“生成”菜单：单击**“生成”\/“配置管理器”**，然后选择**“调试”**或**“发布”**。  
  
2.  在工具栏上，从**“解决方案配置”**列表框选择**“调试”**或**“发布”**。  
  
     ![工具栏生成配置](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Express 版中不提供此工具栏。  您可以使用**“生成解决方案 F6”**和**“启动调试 F5”**菜单项来选择配置。  
  
## 请参阅  
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)   
 [C\+\+ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C\# 调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [如何：创建和编辑配置](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/zh-cn/0440b300-0614-4511-901a-105b771b236e)