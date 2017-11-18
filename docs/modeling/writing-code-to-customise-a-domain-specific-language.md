---
title: "编写代码以自域特定语言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2d456f84078e54694deb11fda0082ac40d278dd2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>编写代码以自定义域特定语言
本部分演示如何使用自定义代码来访问、 修改或创建域特定语言模型。  
  
 有几个可以在其中编写适用于 DSL 代码的上下文：  
  
-   **自定义命令。** 你可以创建命令，用户可以调用通过右键单击关系图中，并且其可以修改模型。 有关详细信息，请参阅[如何： 向快捷菜单添加命令](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。  
  
-   **验证。** 你可以编写代码，用于验证在模型处于正确状态。 有关详细信息，请参阅[域特定语言中的验证](../modeling/validation-in-a-domain-specific-language.md)。  
  
-   **重写默认行为。** 你可以修改从 DslDefinition.dsl 生成的代码的许多方面。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。  
  
-   **文本转换。** 你可以编写包含访问模型，并生成一个文本文件，例如，若要生成程序代码的代码的文本模板。 有关详细信息，请参阅[从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
-   **其他 Visual Studio 扩展。** 你可以编写单独的 VSIX 扩展的读取和修改模型。 有关详细信息，请参阅[如何： 从在程序代码中的文件打开模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 在 DslDefinition.dsl 中定义的类的实例保留在调用的数据结构*内存中存储*(IM) 或*存储*。 你始终在 DSL 中定义的类需要存储作为自变量的构造函数。 例如，如果 DSL 定义一个名为示例类：  
  
 `Example element = new Example (theStore);`  
  
 保持对象 （而不是仅为普通对象） 存储区中提供以下几个好处。  
  
-   **事务**。 你可以进行分组一的系列成事务的相关更改：  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     如果异常过程中发生更改，以便不执行最终的 commit （），应用商店将重置为其以前的状态。 这可帮助你确保错误不会处于不一致状态中离开模型。 有关详细信息，请参阅[导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
-   **二进制关系**。 如果你定义两个类之间的关系，在两端的实例将具有一个属性，导航到另一端。 两个端点始终保持同步。 例如，如果用名为父项和子项的角色定义 parenthood 关系时，你可以编写：  
  
     `John.Children.Add(Mary)`  
  
     下面的表达式都现在成立：  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     此外可以通过编写获得相同的效果：  
  
     `Mary.Parents.Add(John)`  
  
     有关详细信息，请参阅[导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
-   **规则和事件**。 你可以定义激发时指定更改的规则。 使用规则，例如，要保留在关系图上的形状就提供的模型元素最新。 有关详细信息，请参阅[响应和传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
-   **序列化**。 存储区提供了一种标准方式进行序列化到文件包含的对象。 你可以自定义序列化和反序列化的规则。 有关详细信息，请参阅[自定义文件存储和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)。  
  
## <a name="see-also"></a>另请参阅  
 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)