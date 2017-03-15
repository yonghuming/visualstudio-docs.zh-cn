---
title: "对函数行为进行批注 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 对函数行为进行批注
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

除批注 [函数参数和返回值](../code-quality/annotating-function-parameters-and-return-values.md)外，可以使用批注来为整个函数的属性。  
  
## 功能批注  
 下列注意事项适用于整个函数并描述行为或将需要为 true。  
  
|批注|说明|  
|--------|--------|  
|`_Called_from_function_class_(name)`|没有单独用于突出；相反，它将使用 `_When_` 的谓词的注释。  有关详细信息，请参阅[指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)。<br /><br /> `name` 参数是一中还显示有一些函数声明的一个 `_Function_class_` 注释的任意字符串。  `_Called_from_function_class_` 返回非零，则当前分析函数的批注使用具有相同 `name`的 `_Function_class_` 值；否则，返回零。|  
|`_Check_return_`|注释一个返回值，调用方应该检查代码。  如果函数中无效上下文，调用检查器报告错误。|  
|`_Function_class_(name)`|`name` 参数为由用户指定的任意字符串。它在其他命名空间是不同的命名空间。  函数、函数指针或函数指针类型，最 usefully\-a 能属于指定为一个或多个函数类。|  
|`_Raises_SEH_exception_`|杂始终引发结构化异常处理程序 \(SEH\) 异常，以及 `_When_` 和 `_On_failure_` 条件的函数。  有关详细信息，请参阅[指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|  
|`_Maybe_raises_SEH_exception_`|批注可以选择引发 SEH 异常，以及 `_When_` 和 `_On_failure_` 条件的函数。|  
|`_Must_inspect_result_`|批注所有输出值，包括全局变量、参数和返回值。如果中批注对象的值随后进行检查，分析程序所报告错误。“选中”包括是否在 case 表达式，分配给输出参数或全局，或作为参数传递。对于返回值，`_Must_inspect_result_` 暗指 `_Check_return_`。|  
|`_Use_decl_annotations_`|在函数定义上 \(aka 函数体\) 来注释使用位置列表标题中。 在使用 `_Use_decl_annotations_` 时，将出现在同一函数的范围标头使用的注释时，它们也是在具有 `_Use_decl_annotations_` 的注释定义。|  
  
## 成功\/失败批注  
 当函数失败时，其结果可能与函数时成功不完整的结果或与不同。在下面的列表中说明提供了表示失败行为。若要使用这些注释，您必须启用它们确定成功；因此，需要 `_Success_` 注释。注意 `NTSTATUS` 和 `HRESULT` 已具有一个 `_Success_` 注释生成到；但是，在中，如果指定您自己的 `NTSTATUS` 上的 `_Success_` 说明或 `HRESULT`，它重写内置注释。  
  
|批注|说明|  
|--------|--------|  
|`_Always_(anno_list)`|等效于 `anno_list _On_failure_(anno_list)`;即在 `anno_list` 的注释应用函数是否成功。|  
|`_On_failure_(anno_list)`|在 typedef 的 `_Return_type_success_` 是使用时，`_Success_` 也用于显式批注函数的任意或隐式。  在 `_On_failure_` 注释位于函数参数或返回值时，将 \(anno\) 的每个注释的 `anno_list` 行为，就好像该代码为 `_When_(!expr, anno)`，其中 `expr` 是 `_Success_` 参数为必需的说明。  这意味着 `_Success_` 的隐式应用于的所有后期条件的不适用于 `_On_failure_`。|  
|`_Return_type_success_(expr)`|应用为 typedef。  指示该类型返回，并且不显式将 `_Success_` 的所有函数批注，就像其 `_Success_(expr)`。  `_Return_type_success_` 基于函数或函数指针的 typedef 无法使用。|  
|`_Success_(expr)`|`expr` 是为右值的表达式。  在 `_Success_` 注释存在于函数声明或定义时，每一注释上的 \(`anno`\) 函数和在后期条件行为，就好像该代码为 `_When_(expr, anno)`。  在 `_Success_` 注释的函数可能只能使用，而不对其参数或返回类型。  可以具有多对函数的一个 `_Success_` 注释，因此，它无法在任何 `_When_`、`_At_`或 `_Group_`。  有关详细信息，请参阅[指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|  
  
## 请参阅  
 [使用 SAL 批注以减少 C\/C\+\+ 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [内部函数](../code-quality/intrinsic-functions.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)