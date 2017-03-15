---
title: "图形诊断捕获方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea21995d-0241-412e-8f62-600c3794247f
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# 图形诊断捕获方法
此处插入介绍。  
  
## 捕获方法  
 在 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 中，DirectX 11.2 运行时可代表调试工具（例如图形诊断）从内部捕获图形信息，这种方法称为*可靠捕获*。  在此支持添加到 DirectX 运行时之前，可通过截获某些 DirectX 函数调用，以在将这些调用转发到 DirectX 的过程完成之前记录参数和其他信息捕获图形信息，这种方法称为*旧版捕获*。  
  
 因为 DirectX 运行时独自负责捕获 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 中的图形信息，所以无需更新旧版捕获即可支持 DirectX 11.2；因此，将弃用旧版捕获。  但是，因为 DirectX 11.2 运行时不支持低于 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 的 Windows 版本，所以 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 仍然支持对面向 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 和 [!INCLUDE[win7](../debugger/includes/win7_md.md)] 的应用使用旧版捕获。  
  
 这两种方法都将记录相似的信息，并且不会更改捕获图形信息或使用图形诊断工具的方式。  
  
### 可靠捕获  
 可靠捕获支持 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]、[!INCLUDE[win81](../debugger/includes/win81_md.md)] 和 Windows Phone 8.1 上的 [!INCLUDE[winblue_winrt_2](../debugger/includes/winblue_winrt_2_md.md)] 图形诊断。  它通过 DirectX 11.2 支持 DirectX 10.0，并且可以捕获有关 Direct3D 11.2 新功能的图形信息（例如，磁贴资源）。  但是，它无法完全支持所有 Direct3D 11.2 功能，例如，你无法调试使用 HLSL 着色器链接功能创建的 HLSL 着色器。  可靠捕获使用新的捕获 API 以支持其编程捕获方案。  
  
### 旧版捕获  
 旧版捕获支持 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]、Windows RT 8 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 上的 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 和 [!INCLUDE[win7](../debugger/includes/win7_md.md)] 图形诊断。  它通过 DirectX 11.1 支持 DirectX 10.0。  旧版捕获不支持任何 Direct3D 11.2 功能，已弃用旧版捕获，不可使用可靠捕获的方案除外。  旧版捕获使用在 `vsgcapture.h` 头文件中定义的捕获 API 支持其编程捕获方案。  这种编程捕获也已弃用，不可使用可靠捕获的方案除外。  
  
## 请参阅  
 [捕获图形信息](../debugger/capturing-graphics-information.md)   
 [演练：捕获图形信息](../debugger/walkthrough-capturing-graphics-information.md)