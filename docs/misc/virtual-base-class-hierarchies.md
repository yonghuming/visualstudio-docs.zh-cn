---
title: "虚拟基类层次结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "虚拟基类的类 [c + +]"
  - "虚拟基类的类层次结构"
  - "派生的类中，类层次结构注意事项"
  - "虚拟基类层次结构中的虚函数"
  - "基本类虚拟"
  - "虚拟基类，层次结构"
  - "层次结构中，虚拟基类"
ms.assetid: d24fda17-f829-48d6-84ec-8100f26bc5cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 虚拟基类层次结构
某些类层次结构的内容很广泛，但也有很多通用的东西。 通用代码在基类中实现，而特定代码在派生类中实现。  
  
 基类建立派生类可用来实现最大功能的协议非常重要。 这些协议通常是使用虚函数实现的。 有时基类为此类函数提供了默认实现。 在类层次结构（如有向非循环图的图示例中的 `Document` 层次结构）（请参阅[单一继承](/visual-cpp/cpp/single-inheritance)）中，两个有用的函数为 `Identify` 和 `WhereIs`。  
  
 当调用时，`Identify` 函数将返回一个适合 document 类型的正确标识：对于 `Book`，`doc->Identify()` 之类的函数调用必须返回 ISBN 编号；但对于 `HelpFile`，返回产品名称和版本号可能更合适。 同样，`WhereIs` 应返回 `Book` 的行和架，但对于 `HelpFile`，它应返回磁盘位置 \- 可能是目录和文件名。  
  
 `Identify` 和 `WhereIs` 函数的所有实现都返回同类信息很重要。 在这种情况下，字符字符串是合适的。  
  
 这些函数将作为虚函数实现，然后使用指向基类的指针进行调用。 对实际代码的绑定在运行时发生，此时将选择正确的 `Identify` 或 `WhereIs` 函数。  
  
## 请参阅  
 [派生类概述](../misc/overview-of-derived-classes.md)