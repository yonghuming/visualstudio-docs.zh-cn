---
title: "CA2223： 成员应是多个返回类型不同 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 312ba498965cea7404e66d15f9136ac9a364da98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223：成员不应只是返回类型不同
|||  
|-|-|  
|TypeName|MembersShouldDifferByMoreThanReturnType|  
|CheckId|CA2223|  
|类别|Microsoft.Usage|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 两个公共或受保护成员具有除返回类型相同的签名。  
  
## <a name="rule-description"></a>规则说明  
 虽然公共语言运行时允许使用返回类型区分其余部分都相同的成员，但是此功能不在公共语言规范中，也不是各种.NET 编程语言的常见功能。 如果成员不只是返回类型相同，开发人员和开发工具可能不正确区分它们。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请更改各成员的设计，以便它们都是唯一仅根据其名称和参数类型，或者不公开这些成员。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 以下示例中，Microsoft 中间语言 (MSIL) 中显示违反此规则的类型。 请注意，不能通过使用 C# 或 Visual Basic.NET 违反此规则。  
  
```  
  
.namespace UsageLibrary  
{  
  .class public auto ansi beforefieldinit ReturnTypeTest  
         extends [mscorlib]System.Object  
  {  
    .method public hidebysig instance int32  
            AMethod(int32 x) cil managed  
    {  
      // Code size       6 (0x6)  
      .maxstack  1  
      .locals init (int32 V_0)  
      IL_0000:  ldc.i4.0  
      IL_0001:  stloc.0  
      IL_0002:  br.s       IL_0004  
  
      IL_0004:  ldloc.0  
      IL_0005:  ret  
    } // end of method ReturnTypeTest::AMethod  
  
    .method public hidebysig instance string  
            AMethod(int32 x) cil managed  
    {  
      // Code size       10 (0xa)  
      .maxstack  1  
      .locals init (string V_0)  
      IL_0000:  ldstr      "test"  
      IL_0005:  stloc.0  
      IL_0006:  br.s       IL_0008  
  
      IL_0008:  ldloc.0  
      IL_0009:  ret  
    } // end of method ReturnTypeTest::AMethod  
  
    .method public hidebysig specialname rtspecialname  
            instance void  .ctor() cil managed  
    {  
      // Code size       7 (0x7)  
      .maxstack  1  
      IL_0000:  ldarg.0  
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()  
      IL_0006:  ret  
    } // end of method ReturnTypeTest::.ctor  
  
  } // end of class ReturnTypeTest  
  
} // end of namespace UsageLibrary  
  
```