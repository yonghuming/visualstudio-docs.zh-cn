---
title: "批注结构和类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Field_size_bytes_part_"
  - "_Field_size_bytes_full_opt_"
  - "_Field_size_bytes_"
  - "_Field_size_opt_"
  - "_Field_size_part_"
  - "_Field_size_bytes_part_opt_"
  - "_Field_range_"
  - "_Field_size_part_opt_"
  - "_Field_size_"
  - "_Field_size_bytes_opt_"
  - "_Struct_size_bytes_"
  - "_Field_size_bytes_full_"
  - "_Field_size_full_"
  - "_Field_size_full_opt_"
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 批注结构和类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

你可以通过使用批注，犹如固定条件批注结构和类成员 — 它们都假定为可在任何函数调用或进入/退出函数，其中涉及该封闭结构到为参数或结果值，则返回 true。  
  
## <a name="struct-and-class-annotations"></a>结构和类批注  
  
-   `_Field_range_(low, high)`  
  
     该字段正在范围 （包括） 从 `low` 到 `high`。  等效于 `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` 通过使用相应的 pre 或 post 条件应用于带批注的对象。  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     具有可写大小以元素 （或字节数） 为指定的字段 `size`。  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     具有可写大小以元素 （或字节数） 为指定的字段 `size`, ，和 `count` 的可读的那些元素 （字节）。  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     具有读取和写入大小以元素 （或字节数） 为指定的字段 `size`。  
  
-   `_Struct_size_bytes_(size)`  
  
     具有读取和写入大小以元素 （或字节数） 为指定的字段 `size`。  
  
     适用于结构或类声明。  表示该类型的有效对象可能大于声明的类型，指定的字节数与 `size`。  例如：  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     以字节为单位的参数的缓冲区大小 `pM` 类型的 `MyStruct *` 则执行要︰  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [使用 SAL 批注以减少 C/c + + 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [内部函数](../code-quality/intrinsic-functions.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)