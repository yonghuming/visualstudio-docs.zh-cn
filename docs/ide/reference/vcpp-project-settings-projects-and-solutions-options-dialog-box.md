---
title: "“选项”对话框 -&gt;“项目和解决方案”-&gt;“VC++ 项目设置” | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VCBuild"
helpviewer_keywords: 
  - "生成 [Visual Studio], 日志"
  - "生成进程 [C++]"
  - "文件 [Visual Studio], 用 C/C++ 编译器生成"
  - "文件扩展名, 用 C 或 C++ 编译器生成"
  - "cl.exe 编译器, 文件扩展名"
  - "扩展名, 用 C 或 C++ 编译器生成"
  - "BuildLog.htm"
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “选项”对话框 -&gt;“项目和解决方案”-&gt;“VC++ 项目设置”
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

此对话框使您可以定义与生成记录和支持文件类型相关的 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目设置。  
  
### 访问此对话框  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  选择**“项目和解决方案”**，再选择**“VC\+\+ 项目设置”**。  
  
## 生成自定义搜索路径  
 指定包含 .rules 文件的目录列表，.rules 文件可帮助您定义项目的生成规则。  
  
## 生成记录  
 **是**  
 产生生成日志文件。  此选项生成 BuildLog.htm，该文件可以在项目的中间文件目录中找到。  每个新生成都覆盖上一个 BuildLog.htm 文件。  
  
 **否**  
 使生成日志文件不产生。  
  
## 生成计时  
 **是**  
 打开生成计时。  如果选择该选项，则将完成生成所花费的时间发送到“输出”窗口。  有关详细信息，请参阅[输出窗口](../../ide/reference/output-window.md)。  
  
 **否**  
 关闭生成计时。  
  
## 隐藏的扩展名  
 指定在启用**“显示所有文件”**时将不在**“解决方案资源管理器”**中显示的文件的文件扩展名。  
  
## 包括的扩展名  
 指定可导入到项目中的文件的文件扩展名。  
  
## 最大并发 C\+\+ 编译数  
 指定用于并行 C\+\+ 编译的最大 CPU 内核数。  
  
## 在日志中显示环境  
 **是**  
 在生成日志文件中列出环境变量。  此选项指定在生成 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目期间将所有环境变量传回生成日志文件中。  
  
 **否**  
 从生成日志文件中排除环境变量。  
  
## 解决方案资源管理器模式  
 **仅显示项目中的文件**  
 将**“解决方案资源管理器”**配置为仅显示项目中的文件。  
  
 **显示所有文件**  
 将**解决方案资源管理器**配置为显示项目中的文件以及磁盘上项目文件夹中的文件。  
  
## 请参阅  
 [生成 C\/C\+\+ 程序](/visual-cpp/build/building-c-cpp-programs)   
 [C\/C\+\+ 生成参考](/visual-cpp/build/reference/c-cpp-building-reference)