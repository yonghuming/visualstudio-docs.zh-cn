---
title: "如何：使用“模块”窗口 | Microsoft Docs"
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
  - "vs.debug.modules"
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
  - "调试器，“模块”窗口"
  - "“模块”窗口"
  - "可执行文件，在调试时显示"
  - "调试 [Visual Studio]，显示模块"
  - "DLL，在调试时显示"
  - "模块，显示"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用“模块”窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  此功能不可用于 SQL 或脚本调试。  
  
 **“模块”**窗口列出程序所使用的 DLL 与 EXE，并显示各个模块的相关信息。  
  
### 在中断模式或运行模式下显示“模块”窗口  
  
-   在**“调试”**菜单上选择**“窗口”**，然后单击**“模块”**。  
  
     默认情况下，**“模块”**窗口按加载顺序对模块进行排序。  但是，可以选择按任意列来排序。  
  
### 按任意列排序  
  
-   单击该列顶部的按钮。  
  
     使用快捷菜单可以在**“模块”**窗口中加载符号或指定符号路径。  
  
## 加载符号  
 在**“模块”**窗口中，可以看到哪些模块加载了调试符号。  这些信息显示在**“符号状态”**列中。  如果该状态显示**“已跳过加载”**、**“无法查找或打开 PDB 文件”**或**“‘包括’\/‘排除’设置禁用了加载功能”**，则你可以指示调试器从 Microsoft 公共符号服务器下载符号，或者从你的计算机上的符号目录加载符号。  有关更多信息，请参阅[指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
#### 手动加载符号  
  
1.  在**“模块”**窗口中，右击还未加载符号的模块。  
  
2.  指向**“加载符号”**，然后单击**“Microsoft 符号服务器”**或**“符号路径”**。  
  
#### 更改符号加载设置  
  
1.  在**“模块”**窗口中右击任一模块。  
  
2.  单击**“符号设置”**。  
  
     你现在可以更改符号加载设置，如[指定符号位置和加载行为](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)中所述。  只有重新启动调试会话，更改才会生效。  
  
#### 为特定模块更改符号加载行为  
  
1.  在**“模块”**窗口中右击所需模块。  
  
2.  指向**“自动符号加载设置”**，然后单击**“始终手动加载”**或**“默认”**。  只有重新启动调试会话，更改才会生效。  
  
## 请参阅  
 [Breaking Execution](http://msdn.microsoft.com/zh-cn/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)   
 [指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)