---
title: "有关域特定语言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: "26"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 3bab0e785dfccddb7d182864a01146fe697b4247
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="about-domain-specific-languages"></a>关于域特定语言
与 C# 或 UML 等通用语言，不同的域特定语言 (DSL) 可用于表达特定问题空间或域中的语句。  
  
 已知 Dsl 包括正则表达式和 SQL。 每个 DSL 是比好得多通用的语言为说明文本字符串或数据库，但差很多用于描述自己范围以外的想法的操作。 各个行业也有其自己 Dsl。 例如，在电信行业中，调用的说明语言广泛用于电话调用中，指定状态的序列和在无线旅行行业 DSL 用于描述机票预定的标准。  
  
 你的业务和项目也处理有特殊套无法用 DSL 描述的概念。 例如，你可以定义这些应用程序之一的 DSL:  
  
-   在网站的导航路径的计划。  
  
-   电子元件的接线图。  
  
-   传送带和行李处理机场的设备的网络。  
  
 DSL 设计时，你定义*域类*为每个域，如网页、 lamp 或机场签入服务台中的重要概念。 你定义*域关系*如超链接、 网络或将概念连接在一起的传送带。  
  
 DSL 的用户创建*模型。* 模型是*实例*的 DSL。 例如，这些主题描述特定网站或特定设备，或行李处理系统中特定机场连结。  
  
 你的用户可以查看模型作为关系图或 Windows 窗体。 模型还可以作为 XML 使用，即如何存储它们。 DSL 定义时，你定义如何在用户的屏幕上会出现的每个域类和关系的实例。 典型 DSL 显示为图标或连接箭头的矩形的集合。  
  
 下图显示在图表 DSL 小模型：  
  
 ![都铎王朝家谱模型](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>你可以使用 Dsl 做什么  
 典型的应用程序的 DSL 是生成程序代码或其他项目。 DSL 定义时，你可以定义*文本模板*，读取的 DSL 模型和生成文本文件。  
  
 例如，你可以编写可采用机场计划并生成行李处理，以及介绍计划的用户文档的某些软件的一部分的模板。  
  
 DSL 定义后，可以将其分发给其他用户可以在自己的计算机上安装它。 DSL 的用户可以创建和编辑中的模型[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 你还可以定义菜单命令和其他工具，可帮助用户编辑 DSL，验证约束来帮助确保正确，使用 DSL 的并可帮助用户项模板创建的新实例。 你可以包装一个或多个 Dsl 及其工具和其他[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]作为集成包扩展。  
  
 通常情况下，开发团队必须编写为有好几种产品类似的代码时创建的域特定语言。 例如，专用化在行李处理系统中的公司可能定义行李跟踪 DSL 从中它们可能会产生一些每个安装的代码。 DSL 的优点是，它可以理解的客户，从它生成的代码是可靠的并且，系统可以快速更新如果客户的需求更改。  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]允许你创建域特定语言具有图形设计器和你自己的关系图表示法，并随后使用语言生成相应的源代码中，每个项目。  
  
## <a name="domain-specific-development"></a>特定于域的开发  
 域特定开发是识别的应用程序使用一种域特定语言，然后构造语言，并将其部署到应用程序开发人员可以建模部分的过程。 开发人员使用的域特定语言构造特定于其应用程序的模型，使用的模型来生成源代码，，然后使用源代码开发的应用程序。  
  
## <a name="aspects-of-graphical-domain-specific-development"></a>图形的特定于域的开发方面  
 图形的域特定语言必须包括以下功能：  
  
-   Notation  
  
-   域模型  
  
-   项目生成  
  
-   序列化  
  
-   与 Visual Studio 的集成  
  
### <a name="notation"></a>Notation  
 域特定语言必须具有一组相当小，可以轻松地定义和扩展，以表示特定于域的构造的元素。 一种表示法由形状，表示的元素和连接器，表示元素，请在图形关系图面之间的关系组成。 在[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，形状可以扩展和优化，以表示你的域特定语言的元素。  
  
### <a name="domain-model"></a>域模型  
 域特定语言必须组合元素和它们为连贯的语法之间的关系的集。 它还必须定义组合的元素和关系是否有效。 例如，编程语言通常会阻止循环继承，在其中一个类派生自第二个类和第二个类派生自的第一个类。 约束还可以用于表示业务逻辑，例如，某个人但不能为自己的依赖。 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]使用约束 express 的各种域特定语言最需要的限制。  
  
### <a name="artifact-generation"></a>项目生成  
 域特定语言的主要用途之一是生成的项目，例如，源代码、 XML 文件或某些其他可用的数据。 通常情况下，模型中的更改意味着项目中的更改。 你可以使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]生成项目并重新生成它们时将模型更改。  
  
### <a name="serialization"></a>序列化  
 域特定语言必须保留在某种形式的可编辑、 保存、 关闭，并重新加载。 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]使用 XML 格式，你可以定义和自定义如何序列化或保持你的域特定语言。  
  
### <a name="integration-with-visual-studio"></a>与 Visual Studio 的集成  
 因为[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]中托管[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，它扩展了许多[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]窗口和控件。 它还允许你自定义菜单命令、 工具箱项，以及用户界面的其他元素的行为。  
  
 你还可以为您的域特定语言创建模型总线适配器。 此适配器，可以引用一个模型和模型，并允许你编写代码可访问和更新的 DSL 实例内的元素。 通过使用功能强大的模型总线机制，你可以编写[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用多个模型的扩展。 你还可以编写使用模型的独立应用程序。 有关详细信息，请参阅[集成模型通过使用 Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。  
  
## <a name="benefits-of-domain-specific-development"></a>特定于域的开发的优点  
 域特定语言可以提供以下好处：  
  
-   包含完全适应问题空间的构造。  
  
     与通用语言，不同的域特定语言元素和包含直接表示问题空间的逻辑关系。 例如，保险策略应用程序必须包括策略和声明的元素。 域特定语言，使得易于设计的应用程序，并查找和更正错误的逻辑。  
  
-   使非开发人员以及人员： 不知道了解的总体设计的域。  
  
     通过使用图形的域特定语言，你可以创建可视表示形式的域，以便非开发人员能够轻松地理解应用程序的设计。  
  
-   便于创建最终应用程序的原型。  
  
     开发人员可以使用它们的模型生成创建原型应用程序，它们可显示给客户端的代码。  
  
## <a name="the-process-of-domain-specific-development"></a>特定于域的开发过程  
 使用域特定语言的大多数软件开发团队执行以下步骤创建和使用其模型：  
  
-   团队区分永远不会更改的部分中的域的变量部分。  
  
-   开发人员编写的固定部分的代码，并且保留的变量部分的扩展点。  
  
-   首席软件开发人员或架构师创建包含的固定部分的域和的变量部分的扩展点的设计模式的域特定语言。  
  
-   首席软件开发人员或架构师将部署的团队生成的各种应用程序的开发人员的域特定语言。  
  
-   每个开发人员创建的模型可以应用于特定应用程序。