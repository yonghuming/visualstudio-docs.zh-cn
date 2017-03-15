---
title: "重载概述 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "函数重载，关于函数重载"
  - "运算符重载，关于运算符重载"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 重载概述
使用 C\+\+ 语言，您可以重载函数和运算符。 重载是为同一范围内的某个给定函数名称提供多个定义的做法。 编译器仍将根据用于调用它的参数来选择适当版本的函数或运算符。 例如，函数 max 被视为重载函数。 它可用于代码中，如下所示：  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 在第一个函数调用中（其中，将请求 `int` 类型的两个变量的最大值），将调用 `max( int, int )` 函数。 但是，在第二个函数调用中，参数为 `double` 类型，因此将调用函数 `max( double, double )`。  
  
## 请参阅  
 [重载 （c \+ \+）](../misc/overloading-cpp.md)