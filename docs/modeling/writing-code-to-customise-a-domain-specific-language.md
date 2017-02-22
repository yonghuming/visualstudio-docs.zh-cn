---
title: "编写代码以自域特定语言 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言编程"
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
caps.handback.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 编写代码以自域特定语言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节在域特定语言 \(dsl\) 演示如何使用自定义代码访问，修改或创建模型。  
  
 可以编写用于 DSL 一起使用的一些上下文:  
  
-   **自定义命令。**可以创建用户可以通过右击调用关系图，因此，可以修改模型的命令。  有关更多信息，请参见 [如何：向快捷菜单中添加命令](../Topic/How%20to:%20Add%20a%20Command%20to%20the%20Shortcut%20Menu.md)。  
  
-   **验证。**您可以验证的代码模型在一个正确的状态。  有关更多信息，请参见 [域特定语言中的验证](../modeling/validation-in-a-domain-specific-language.md)。  
  
-   **重写默认行为。**可以修改从 DslDefinition.dsl 生成代码的许多方面。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。  
  
-   **文本转换。**可以编写包含代码访问模型并生成一个文本文件，例如生成程序代码的文本模板。  有关更多信息，请参见 [从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
-   **其他 Visual Studio 扩展。**您可以读取和修改模型编写单独的 VSIX 扩展。  有关更多信息，请参见[如果：在程序代码中从文件打开模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 在 DslDefinition.dsl 定义类的实例在调用内存 *存储 \(IMS\)* 或存储的数据结构中保留 *。* 在 DSL 定义的类始终采用作为参数传递给构造函数。  例如， DSL，如果定义了一个名为 Example 的类:  
  
 `Example element = new Example (theStore);`  
  
 将对象保留在单元 \(而不是普通对象\) 提供一些好处。  
  
-   **事务**。  可将一系列相关更改为事务:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     在更改期间，如果发生异常，因此，最终 Commit\(\) 未实现，存储将重置为其以前的状态。  这有助于确保，错误处于不一致状态不能使该模型保留。  有关更多信息，请参见 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
-   **二进制关系**。  如果您定义两个类之间的关系，实例在两端具有导航到另一端的属性。  两端总是同步的。  例如，因此，如果您定义了名为 Parents 和子级的角色的框架标识关系，可以编写:  
  
     `John.Children.Add(Mary)`  
  
     下面的两个表达式现在为 true:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     您可以通过编写还获得相同的效果:  
  
     `Mary.Parents.Add(John)`  
  
     有关更多信息，请参见 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
-   **规则和事件**。  可以定义激发的规则，只要指定的更改。  它们的规则用于，例如，在关系图上的形状最新的模型元素。  有关更多信息，请参见 [响应并传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
-   **序列化**。  存储为其包含到文件的标准方式序列化对象。  您可以自定义序列化和反序列化的规则。  有关更多信息，请参见 [自定义文件存储和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)。  
  
## 请参阅  
 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)