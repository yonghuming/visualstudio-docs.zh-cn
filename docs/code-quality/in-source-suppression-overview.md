---
title: "源代码中禁止显示概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f35833df8e84a4e4caba8fd46f8daea8dd5119a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="in-source-suppression-overview"></a>“源代码中禁止显示”概述
在源代码中禁止显示是能够禁止显示或忽略托管代码中的代码分析冲突通过添加**SuppressMessage**属性设为导致冲突的代码段。 **SuppressMessage**属性是它仅当在编译时定义 CODE_ANALYSIS 编译符号，托管的代码程序集的 IL 元数据中包括条件属性。  
  
 在 C++/CLI 中，在头文件中使用宏 CA_SUPPRESS_MESSAGE 或 CA_GLOBAL_SUPPRESS_MESSAGE 来添加特性。  
  
 不应在发布版本使用在源代码中禁止显示以防止意外传送在源代码中禁止显示元数据。 由于在源代码中禁止显示的处理开销，你的应用程序的性能可以通过也会降低包括在源代码中禁止显示元数据。  
  
> [!NOTE]
>  你不需要移交代码这些特性亲自。 有关详细信息，请参阅[如何： 通过使用菜单项禁止显示警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。 菜单项不可用 c + + 代码。  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage 特性  
 当您右键单击中的某个代码分析警告**错误列表**，然后单击**禁止显示消息**、 **SuppressMessage**属性会被添加在代码中或为项目的全局禁止显示文件。  
  
 **SuppressMessage**属性具有以下格式：  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 其中：  
  
-   **规则类别**-定义了该规则的类别。 有关代码分析规则类别的详细信息，请参阅[为托管代码警告的代码分析](../code-quality/code-analysis-for-managed-code-warnings.md)。  
  
-   **规则 Id**的规则的标识符。 支持包括同时规则标识符的短期和长期名称。 短名称是 CAXXXX;全称是 CAXXXX:FriendlyTypeName。  
  
-   **两端对齐**-用于记录禁止显示消息的原因的文本。  
  
-   **消息 Id** -每条消息的问题的唯一标识符。  
  
-   **作用域**-在其取消该警告的目标。 如果未指定目标，则将它设置为目标的属性。 支持的作用域包括：  
  
    -   模块  
  
    -   命名空间  
  
    -   资源  
  
    -   类型  
  
    -   成员  
  
-   **目标**-的标识符，用于以指定在其取消该警告的目标。 它必须包含完全限定的项名称。  
  
## <a name="suppressmessage-usage"></a>SuppressMessage 使用情况  
 在向其级别取消代码分析警告的实例**SuppressMessage**应用特性。 这样做的目的是紧密耦合对代码的禁止显示信息发生了冲突。  
  
 禁止显示的一般形式包括规则类别和其中包含的可选的用户可读表示形式的规则名称的规则标识符。 例如，  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 如果有尽量减少在源代码中禁止显示元数据的严格性能原因，可以省略规则名称本身。规则类别和其规则 ID 一起构成足够唯一的规则标识符。 例如，  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 由于可维护性问题的缘故，不建议使用此格式。  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>禁止在方法体中显示多个冲突  
 特性仅应用于方法和不能嵌入方法体中。 但是，你可以为消息 ID 来区分多个出现的冲突的方法内指定的标识符。  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>生成的代码  
 托管的代码编译器和某些第三方工具生成代码以加快代码的开发。 将出现在源文件中的编译器生成的代码通常将标有**GeneratedCodeAttribute**属性。  
  
 你可以选择是否要取消显示代码分析警告和错误生成的代码。 有关如何禁止显示此类警告和错误的信息，请参阅[如何： 禁止显示生成的代码的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。  
  
 请注意，代码分析将忽略**GeneratedCodeAttribute**当应用于整个程序集或单个参数。 这些情况下很少发生。  
  
## <a name="global-level-suppressions"></a>全局级禁止显示  
 托管的代码分析工具可检查是否**SuppressMessage**在程序集、 模块、 类型、 成员或参数级别应用的属性。 它还会引发对资源和命名空间冲突。 必须在全局级别应用这些冲突作用域和目标。 例如，以下消息禁止显示命名空间冲突：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  禁止显示警告，其中包含命名空间范围内时，它禁止显示针对该命名空间本身的警告。 它不会取消对类型的命名空间中的警告。  
  
 可以通过指定一个显式的作用域表示任何抑制。 在全局级别必须位于这些禁止显示。 不能指定成员级别禁止显示的修饰类型。  
  
 全局级禁止显示是它们取消引用未映射到显式提供的用户源的编译器生成代码的消息的唯一方法。 例如，下面的代码将取消违反了针对编译器发出的构造函数：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  目标始终包含完全限定的项名称。  
  
## <a name="global-suppression-file"></a>全局禁止显示文件  
 全局禁止显示文件维护全局级禁止显示或不指定目标的禁止显示。 例如，程序集级冲突的禁止显示存储在此文件。 此外，某些 ASP.NET 禁止显示功能存储在此文件中，是因为项目级别设置不可用于窗体背后的代码。 全局禁止显示被创建并添加到你的项目选择的第一个时间**在项目禁止显示文件**选项**禁止显示消息**命令，在错误列表窗口。 有关详细信息，请参阅[如何： 通过使用菜单项禁止显示警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Diagnostics.CodeAnalysis>