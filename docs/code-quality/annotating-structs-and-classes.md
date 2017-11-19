---
title: "批注结构和类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 651108f2c917fb81857e3466384a9bfebada4a4b
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="annotating-structs-and-classes"></a>批注结构和类
还可以通过使用批注，即可充当固定协定批注结构和类成员，它们将假定应满足的任何函数调用或函数入口/出口涉及该封闭结构作为参数或结果值。  
  
## <a name="struct-and-class-annotations"></a>结构和类批注  
  
-   `_Field_range_(low, high)`  
  
     该字段正在从 （含） 范围`low`到`high`。  等效于`_Satisfies_(_Curr_ >= low && _Curr_ <= high)`通过使用适当的 pre 或 post 条件应用于批注对象。  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     具有在元素 （或字节） 为指定的可写大小的字段`size`。  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     具有在元素 （或字节） 为指定的可写大小的字段`size`，和`count`是否都可读这些元素 （字节）。  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     具有读取和写入大小在元素 （或字节） 为指定的字段`size`。  
  
-   `_Struct_size_bytes_(size)`  
  
     具有读取和写入大小在元素 （或字节） 为指定的字段`size`。  
  
     适用于结构或类声明。  指示该类型的有效对象可能会大于声明的类型，使用指定的字节数`size`。  例如：  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        ...  
    };  
  
    ```  
  
     以字节为单位的参数的缓冲区大小`pM`类型的`MyStruct *`然后将其视为：  
  
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