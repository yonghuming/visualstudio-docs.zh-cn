---
title: "CA2233：运算不应溢出 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2233：运算不应溢出
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某方法执行算术运算，但没有预先验证操作数以防止溢出。  
  
## 规则说明  
 如果未首先验证操作数以确保运算结果不会超出所涉及数据类型的允许值范围，则不应执行算术运算。  取决于执行上下文和涉及的数据类型，算术溢出可能导致 <xref:System.OverflowException?displayProperty=fullName> 或结果的最高有效位被丢弃。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请在执行运算前验证操作数。  
  
## 何时禁止显示警告  
 如果操作数的可能值永远不会导致算术运算溢出，则可以安全地禁止显示与该规则有关的警告。  
  
## 冲突的示例  
  
### 说明  
 下面示例中的方法使用一个与此规则冲突的整数。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 要求禁用**移除**整数溢出选项来激发此规则。  
  
### 代码  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### 注释  
 如果向此示例中的方法传递了 <xref:System.Int32.MinValue?displayProperty=fullName>，则操作将下溢。  这会导致结果的最高有效位被丢弃。  下面的代码演示这一过程。  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Output  
  
```  
2147483647  
```  
  
## 使用输入参数验证进行修复  
  
### 说明  
 下面的示例通过验证输入值来修复前面的冲突。  
  
### 代码  
 [!CODE [FxCop.Usage.OperationOverflowFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed#1)]  
  
## 使用 Checked 块进行修复  
  
### 说明  
 下面的示例通过封装 Checked 块中的操作来修复前面的冲突。  如果操作导致溢出，将引发 <xref:System.OverflowException?displayProperty=fullName>。  
  
 请注意，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 不支持 Checked 块。  
  
### 代码  
 [!CODE [FxCop.Usage.OperationOverflowChecked#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked#1)]  
  
## 打开 Checked 运算上溢\/下溢  
 如果在 C\# 中打开 Checked 运算上溢\/下溢，则等效于封装 Checked 块中的每个整数运算。  
  
 **在 C\# 中打开 Checked 运算上溢\/下溢**  
  
1.  在**“解决方案资源管理器”**中，右击项目并选择**“属性”**。  
  
2.  选择**“生成”**选项卡并单击**“高级”**。  
  
3.  选择**“检查运算上溢\/下溢”**并单击**“确定”**。  
  
## 请参阅  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C\# 运算符](/dotnet/csharp/language-reference/operators/index)   
 [Checked 和 Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)