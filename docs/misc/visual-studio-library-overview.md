---
title: "Visual Studio 库概述 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 库, 概述"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Visual Studio 库概述
Visual Studio 库是一组简化的 Vspackage 的创建基于模板的 C\+\+ 类在本机 C\+\+ 的。  Visual Studio 库包括完整源代码，为一组 C\+\+ 头文件。  头文件中 *Visual Studio SDK 安装路径*\\VisualStudioIntegration \\Common\\Source\\CPP\\VSL\\Include \\ 安装。  
  
> [!NOTE]
>  Visual Studio 库依赖于它的 \(ATL\)活动模板库 \(atl\) 支持 COM 对象。  有关更多信息，请参见 [ATL 介绍](/visual-cpp/atl/introduction-to-atl)。  
  
 Visual Studio 库测试，对于自己的代码以及代码的框架支持。  某个单元测试是包含的，如下所示:  
  
-   Visual Studio 库单元 *Visual Studio SDK 安装路径*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\UnitTest \\ 测试安装。  
  
-   单元测试的基类测试代码在 *Visual Studio SDK 安装路径*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include\\VSLUnitTest .h。  
  
 常用的 COM 和 Visual Studio 接口的模拟实现在头文件中， VSLMockSystemInterfaces.h 和 VSLMockVisualStudioInterfaces.h，在 *Visual Studio SDK 安装路径*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include \\ 安装。  
  
## 请参阅  
 [使用 Visual Studio 库开发 VSPackages](../misc/developing-vspackages-by-using-the-visual-studio-library.md)