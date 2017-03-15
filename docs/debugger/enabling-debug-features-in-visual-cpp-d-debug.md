---
title: "在 Visual C++ 中启用调试功能 (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/D_DEBUG 编译器选项 [C++]"
  - "_DEBUG 宏"
  - "断言, 启用调试功能"
  - "D_DEBUG 编译器选项"
  - "调试版本, MFC"
  - "调试 [C++], 启用调试功能"
  - "调试 [MFC], 启用调试功能"
  - "MFC 库, 调试版本"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在 Visual C++ 中启用调试功能 (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 中，如果在编译程序时定义了 **\_DEBUG** 符号，则将启用某些调试功能（如断言）。  可以用下列两种方法之一定义 **\_DEBUG**：  
  
-   在源代码中指定 **\#define \_DEBUG**，或  
  
-   指定 **\/D\_DEBUG** 编译器选项。（如果是在 Visual Studio 中使用向导创建项目，则 **\/D\_DEBUG** 将在“调试”配置中自动定义。）  
  
 在定义了 **\_DEBUG** 后，编译器将编译包围在 **\#ifdef \_DEBUG** 和 `#endif` 内的代码段。  
  
 MFC 程序的调试配置必须与 MFC 库的调试版本链接。  MFC 头文件根据您定义的符号（如 **\_DEBUG** 和 **\_UNICODE**）确定要链接的 MFC 库的正确版本。  有关详细信息，请参见 [MFC 库版本](/visual-cpp/mfc/mfc-library-versions)。  
  
## 请参阅  
 [调试本机代码](../debugger/debugging-native-code.md)   
 [C\+\+ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)