---
title: "重载函数的地址 | Microsoft Docs"
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
  - "地址 [c + +] 重载函数"
  - "返回重载地址 [c + +]"
  - "函数重载函数地址"
  - "此指针，重载函数"
ms.assetid: e7913e65-a295-445d-b2b0-1e60f8dfbc54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 重载函数的地址
在没有自变量的情况下使用函数名称将返回该函数的地址。 例如：  
  
```  
int Func( int i, int j );  
int Func( long l );  
  
...  
  
int (*pFunc) ( int, int ) = Func;  
```  
  
 在前面的示例中，选择了 `Func` 的第一个版本，然后将其地址复制到 `pFunc` 中。  
  
 编译器使用参数列表查找与目标的参数完全匹配的函数，从而确定要选择的函数的版本。 重载函数声明中的参数与以下项之一匹配:  
  
-   要初始化的对像（如前面的示例所示）  
  
-   赋值语句的左侧  
  
-   函数的形参  
  
-   用户定义的运算符的形参  
  
-   函数返回类型  
  
 如果未找到完全匹配项，采用函数地址的表达式将不明确并会产生错误。  
  
 请注意，尽管前面的示例中使用了非成员函数 `Func`，但当采用重载成员函数的地址时，仍将应用相同的规则。  
  
## 请参阅  
 [重载 （c \+ \+）](../misc/overloading-cpp.md)