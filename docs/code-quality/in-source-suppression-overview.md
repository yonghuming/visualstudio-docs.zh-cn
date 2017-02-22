---
title: "“源代码中禁止显示”概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "禁止显示源, 代码分析"
  - "代码分析, 禁止显示源"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “源代码中禁止显示”概述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

源代码中禁止显示是指通过将 **SuppressMessage** 特性添加到导致冲突的代码段禁止显示或忽略托管代码中代码分析冲突的功能。  **SuppressMessage** 特性是一个条件特性，只有在编译时定义了 CODE\_ANALYSIS 编译符号时，它才会包含在托管代码程序集的 IL 元数据中。  
  
 在托管 C\+\+ 中，使用头文件中的宏 CA\_SUPPRESS\_MESSAGE 或 CA\_GLOBAL\_SUPPRESS\_MESSAGE 来添加特性。  
  
 不应在发布版本中使用源代码中禁止显示功能，以避免意外地提供源代码中禁止显示的元数据。  由于源代码中禁止显示的处理成本，通过包括源代码中禁止显示的元数据，也会降低应用程序的性能。  
  
> [!NOTE]
>  您不需要亲自为这些特性手动编写代码。  有关详细信息，请参阅[如何：使用菜单项禁止显示警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。  菜单项不适用于 C\+\+ 代码。  
  
## SuppressMessage 特性  
 当您右击**“错误列表”**中的某个代码分析警告再单击**“禁止显示消息”**时，**SuppressMessage** 特性将添加到您的代码中，或者添加到项目的全局禁止显示文件中。  
  
 **SuppressMessage** 特性的格式如下所示：  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 其中：  
  
-   **Rule Category** \- 定义的规则所属的类别。  有关代码分析规则类别的更多信息，请参见[托管代码的代码分析警告](../code-quality/code-analysis-for-managed-code-warnings.md)。  
  
-   **Rule Id** \- 规则的标识符。  同时支持规则标识符的短名称和长名称。  短名称是 CAXXXX；长名称是 CAXXXX:FriendlyTypeName。  
  
-   **Justification** \- 用于记录禁止显示消息的原因的文本。  
  
-   **Message Id** \- 每个消息的问题的唯一标识符。  
  
-   **Scope** \- 在其上禁止显示警告的目标。  如果未指定目标，则设置为特性的目标。  支持的范围包括：  
  
    -   模块  
  
    -   命名空间  
  
    -   资源  
  
    -   类型  
  
    -   成员  
  
-   **Target** \- 用于指定在其上禁止显示警告的目标的标识符。  它必须包含完全限定的项名称。  
  
## SuppressMessage 的用法  
 在应用 **SuppressMessage** 特性的实例的级别上，禁止显示代码分析警告。  执行此操作的目的是为了使禁止显示信息与发生冲突的代码紧密耦合。  
  
 禁止显示的一般形式包括规则类别和一个规则标识符，该标识符包含可选的规则名称的用户可读表示形式。  例如，  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 如果出于严格的性能原因，要求最大程度地减少代码内禁止显示元数据，则可以省略规则名称本身。  规则类别及其规则 ID 一起构成足够唯一的规则标识符。  例如，  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 出于可维护性的原因，建议不要使用该格式。  
  
## 在方法体内禁止显示多个冲突  
 特性只能应用于方法，而不能嵌入到方法体中。  但是，您可以将标识符指定为消息 ID，以便在方法内多次出现冲突时进行区分。  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## 生成的代码  
 托管代码编译器和某些第三方工具会生成代码，以加快代码的开发。  源文件中出现的、由编译器生成的代码通常用 **GenerateCodeAttribute** 特性标记。  
  
 您可以选择是否禁止对生成的代码显示代码分析警告和错误。  有关如何禁止显示此类警告和错误的信息，请参见[如何：禁止显示所生成代码的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。  
  
 请注意，如果 **GeneratedCodeAttribute** 应用于整个程序集或单个参数，代码分析将忽略此属性。  这些情况极少发生。  
  
## 全局级禁止显示  
 托管代码分析工具检查在程序集、模块、类型、成员或参数级应用的 **SuppressMessage** 特性。  它还针对资源和命名空间引发冲突。  这些冲突必须在全局级应用，并且是有范围和目标的。  例如，下面的消息禁止显示命名空间冲突：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  当您禁止显示具有命名空间范围的警告时，将同时禁止显示针对该命名空间本身的警告。  不会禁止显示针对该命名空间内的类型的警告。  
  
 任何禁止显示都可以通过指定一个显式范围来表示。  这些禁止显示必须在全局级启用。  您不能通过修饰某个类型来指定成员级的禁止显示。  
  
 对于引用编译器生成的、并未映射到显式提供的用户源的代码的消息，全局级禁止显示是禁止显示它们的唯一方法。  例如，下面的代码禁止显示针对编译器发出的构造函数的冲突：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  目标始终包含完全限定的项名称。  
  
## 全局禁止显示文件  
 全局禁止显示文件维护全局级禁止显示或未指定目标的禁止显示。  例如，程序集级冲突的禁止显示存储在该文件中。  此外，某些 ASP.NET 禁止显示之所以存储在此文件中，是因为项目级设置对于窗体背后的代码不可用。  首次在“错误列表”窗口中选择**“禁止显示消息”**命令的**“在项目禁止显示文件中”**选项时，将创建全局禁止显示文件并将其添加到您的项目中。  有关详细信息，请参阅[如何：使用菜单项禁止显示警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。  
  
## 请参阅  
 <xref:System.Diagnostics.CodeAnalysis>