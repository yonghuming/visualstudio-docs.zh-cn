---
title: "CA1903：仅使用目标框架中的 API | Microsoft Docs"
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
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1903：仅使用目标框架中的 API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|类别|Microsoft.Portability|  
|是否重大更改|重大更改 \- 当针对外部可见成员或类型的签名激发时。<br /><br /> 非重大更改 \- 当在方法体中激发时。|  
  
## 原因  
 成员或类型将使用 Service Pack 中引入的成员或类型，项目目标框架中未及包括它们。  
  
## 规则说明  
 .NET Framework 2.0 Service Pack 1 和 2、.NET Framework 3.0 Service Pack 1 和 2，以及 .NET Framework 3.5 Service Pack 1 中包括了新的成员和类型。  以 .NET Framework 的主要版本为目标的项目可能会在无意中依赖这些新的 API。  为避免这种依赖性，使用默认情况下没有包括在项目目标框架中的任何新成员和类型时，将激发此规则。  
  
 **目标框架和 Service Pack 的依赖关系**  
  
|||  
|-|-|  
|对于以下目标框架|使用以下框架中引入的成员时将激发规则|  
|.NET Framework 2.0|.NET Framework 2.0 SP1 和 .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1 和 .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|不可用|  
  
 若要更改项目的目标框架，请参见[面向特定的 .NET Framework 版本](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
## 如何解决冲突  
 若要移除对 Service Pack 的依赖，请避免使用所有新成员或类型。  如果此依赖是有意为之，请禁止显示警告或者关闭此规则。  
  
## 何时禁止显示警告  
 如果针对所指定 Service Pack 的依赖不是有意为之，请不要禁止显示此规则发出的警告。  在这种情况下，应用程序可能无法在没有安装此 Service Pack 的系统上运行。  如果此依赖是有意为之，请禁止显示警告或者关闭此规则。  
  
## 示例  
 下面的示例演示使用只在 .NET 2.0 Service Pack 1 中可用的类型 DateTimeOffset 的类。  此示例要求已在项目属性中“目标框架”下拉列表中选择 .NET Framework 2.0。  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## 示例  
 下面的示例将使用的 DateTimeOffset 类型替换为 DateTime 类型，从而解决上面描述的冲突。  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## 请参阅  
 [可移植性警告](../code-quality/portability-warnings.md)   
 [面向特定的 .NET Framework 版本](../ide/targeting-a-specific-dotnet-framework-version.md)