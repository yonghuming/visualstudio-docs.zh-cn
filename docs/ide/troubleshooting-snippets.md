---
title: "疑难解答：代码段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense 代码段, 疑难解答"
  - "IntelliSense 代码段疑难解答"
  - "Visual Basic 疑难解答, IntelliSense 代码段"
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 疑难解答：代码段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense 代码段的问题通常由两个问题引起：已损坏的代码段文件或代码段文件中的错误内容。  
  
## 常见问题  
  
### 代码段无法从文件资源管理器拖入Visual Studio源文件  
  
-   代码段文件中的 XML 可能已损坏。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的**“XML 编辑器”**可以定位 XML 结构中的问题。  
  
-   代码段文件可能不符合代码段架构。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的**“XML 编辑器”**可以定位 XML 结构中的问题。  
  
### 代码存在未突出显示的编译器错误  
  
-   可能缺少项目引用。  检查与此代码段相关的文档。  如果未在计算机中找到此引用，则必须安装此引用。  插入代码段时应在项目中添加所需的任何引用。  如果代码段缺少引用信息，可以将此情形作为一个错误报告给代码段创建者。  
  
-   可能未定义变量。  代码段中的未定义变量应突出显示。  如果未突出显示，则将此情形作为一个错误报告给代码段创建者。  
  
## 请参阅  
 [代码段](../ide/code-snippets.md)