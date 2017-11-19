---
title: "重写和扩展生成的类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: "15"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 81f218f9c0d9cd5d9c6abf8f4f9f0fb78181f4f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="overriding-and-extending-the-generated-classes"></a>重写和扩展生成的类
DSL 定义是一个平台，你可以基于其构建一套强大的基于域特定语言的工具。 许多扩展和改编可以通过重写和扩展从 DSL 定义生成的类。 这些类包括而不仅仅是中 DSL 定义关系图中，已显式定义的域类还有其他类的定义工具箱、 资源管理器、 序列化和等等。  
  
## <a name="extensibility-mechanisms"></a>扩展性机制  
 提供了几种机制，以便您可以扩展生成的代码。  
  
### <a name="overriding-methods-in-a-partial-class"></a>分部类中重写方法  
 分部类定义允许用于在多个位置中定义的类。 这样，你可以从你自己编写的代码将生成的代码。 在你手动编写的代码，你可以重写由生成的代码继承的类。  
  
 例如，如果在 DSL 定义中定义一个名为的域类`Book`，你可以编写将添加重写方法的自定义代码：  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  若要重写方法生成的类中，始终从生成的文件分隔文件中编写代码。 通常情况下，该文件被包含在名为自定义代码的文件夹。 如果更改生成的代码时，它们会丢失时重新生成 DSL 定义中的代码。  
  
 若要发现可以重写何种方法，请键入**重写**在类中后, 跟一个空格。 IntelliSense 工具提示将告诉您何种方法可以重写。  
  
### <a name="double-derived-classes"></a>双派生类  
 大部分中生成的类的方法均继承于一组固定的建模命名空间中的类。 但是，某些方法生成的代码中定义。 通常，这意味着不能重写它们;不能在一个分部类中覆盖在同一个类的另一个分部定义中定义的方法。  
  
 不过，通过设置重写这些方法**生成 Double 派生**域类标志。 要生成此原因两个类，一个轮廓的另一个抽象基类。 所有方法和属性定义在基类中，并仅的构造函数是在派生类中。  
  
 例如，在示例 Library.dsl，`CirculationBook`域类具有`Generates``Double Derived`属性设置为`true`。 为域该类生成的代码包含两个类：  
  
-   `CirculationBookBase`这是一个抽象，它包含所有方法和属性。  
  
-   `CirculationBook`该类派生自`CirculationBookBase`。 它是空的但其构造函数除外。  
  
 若要重写任何方法，您创建派生类的部分定义如`CirculationBook`。 您可以重写生成的方法和从建模 framework 继承的方法。  
  
 与所有类型的元素，包括模型元素、 关系、 形状、 关系图和连接器，可以使用此方法。 你也可以替代的其他生成类的方法。 某些生成 （如 ToolboxHelper 始终） 双派生的类。  
  
### <a name="custom-constructors"></a>自定义的构造函数  
 不能重写构造函数。 即使在双派生类中，构造函数必须在派生类中。  
  
 如果你想要提供自己的构造函数，可以执行此操作通过设置`Has Custom Constructor`DSL 定义中的域类。 当你单击**转换所有模板**，生成的代码将不包括为该类的构造函数。 它包含对缺少的构造函数的调用。 这会导致错误报告，在生成解决方案。 双击错误报告以查看说明您应提供生成的代码中的注释。  
  
 在独立于生成的文件的文件中编写的分部类定义，并提供构造函数。  
  
### <a name="flagged-extension-points"></a>标记的扩展点  
 标记的扩展点是，你可以在其中设置的属性或一个复选框以指示你将提供的自定义方法 DSL 定义中的位置。 自定义的构造函数是一个示例。 其他示例包括设置`Kind`的计算或自定义存储或设置某一域属性**是自定义**连接生成器中的标志。  
  
 在每个情况下，当你设置标志，然后重新生成代码，将导致生成错误。 双击错误以了解说明你需要提供的注释。  
  
### <a name="rules"></a>规则  
 事务管理器允许你定义在其中指定已发生的事件，例如，在属性发生更改的事务结束之前运行的规则。 规则通常用于维护 synchronism 存储区中的不同元素之间。 例如，使用规则以确保关系图显示模型的当前状态。  
  
 根据每个类定义规则，以便无需具有代码用于注册每个对象的规则。 有关详细信息，请参阅[规则传播更改内模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
### <a name="store-events"></a>存储事件  
 建模存储区提供一种事件机制，可用于侦听特定类型的存储，包括添加和删除的元素，更改属性值中的更改和其他操作。 后已更改的事务调用事件处理程序。 通常情况下，这些事件用于更新 store 外的资源。  
  
### <a name="net-events"></a>.NET 事件  
 你可以订阅在形状上的某些事件。 例如，你可以侦听形状上的鼠标单击。 你必须编写订阅的每个对象的事件的代码。 可以在 InitializeInstanceResources() 重写中编写此代码。  
  
 在 ShapeFields，用于在形状上绘制修饰符上生成一些事件。 有关示例，请参阅[如何： 截获点击形状或修饰器](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)。  
  
 这些事件通常不会发生在事务内。 如果你想要在存储中进行更改，你应创建一个事务。