---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

类设计器支持用 `struct` 关键字声明的 C\+\+ 结构。  下面是一个示例：  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 有关使用 `struct` 类型的更多信息，请参见 [struct](/visual-cpp/cpp/struct-cpp)。  
  
 类关系图中的 C\+\+ 结构形状的外观和工作原理与类形状的类似，除了标签显示为**“结构”**之外，各个角是方形而不是圆形的。  
  
|代码元素|类设计器视图|  
|----------|------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 结构|  
  
## 请参阅  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [类和结构](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)