---
title: "与非类型化数据集类型化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 8fda7a1663a8aa9ccbf1f89f2a3b05d74b0a2316
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="typed-vs-untyped-datasets"></a>与非类型化数据集类型
类型化数据集是首先派生自基本的数据集<xref:System.Data.DataSet>类，然后使用从信息**数据集设计器**，其存储在.xsd 文件，以生成一个新的强类型化数据集类。 生成架构 （表、 列和等等） 中的信息并将其编译为此新的数据集类为一组的第一类对象和属性。 因为类型化数据集继承自基类<xref:System.Data.DataSet>类，类型化的类假定所有的功能<xref:System.Data.DataSet>类，并可与将的实例的方法使用<xref:System.Data.DataSet>类作为一个参数。  
  
 非类型化的数据集，与此相反，具有没有相应的内置架构。 如下所示类型化数据集，非类型化数据集包含表、 列和等等 — 但那些仅作为集合公开。 (但是，你手动创建表和其他数据元素中的非类型化数据集后，你可以将导出的数据集的结构为架构使用的数据集的<xref:System.Data.DataSet.WriteXmlSchema%2A>方法。)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>对比中类型化和非类型化数据集的数据访问  
 类型化数据集的类具有顺序的表和列的实际名称对其执行其属性的对象模型。 例如，如果你正在使用类型化数据集，你可以使用类似以下的代码中引用列：  
  
 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]  
  
 与此相反，如果你正在使用非类型化数据集，则是等效的代码：  
  
 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]  
  
 类型化的访问不是仅更易读，但还完全支持通过中的 IntelliSense [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **代码编辑器**。 除了更轻松地使用外，类型化数据集的语法提供类型检查在编译时，极大地缩短中将值分配到数据集成员的错误的可能性。 如果你更改中的列名称你<xref:System.Data.DataSet>类，然后编译你的应用程序，你收到生成错误。 通过双击中的生成错误**任务列表**，你可以直接转到行或引用旧的列名称的代码行。 访问表和列在类型化数据集也是在运行时稍微快一些因为在编译时，不能通过集合在运行时确定访问。  
  
 即使类型化数据集具有很多优点，非类型化数据集可在各种情况。 当任何架构都没有可用数据集时，将为最显而易见的情形。 这可能会发生，例如，如果你的应用程序进行交互的组件，返回的数据集，但是你不知道提前什么是其结构。 同样，有时你正在使用不具有静态、 可预测的结构的数据的时间。 在这种情况下，它是不切实际的使用类型化数据集，因为您将不得不重新生成具有数据结构中的每个更改的类型化数据集类。  
  
 一般来说，有很多时候你可能无可用架构动态创建的数据集。 在这种情况下，数据集是只需在其中你可以保留信息，方便结构，只要数据可以表示关系的方式。 同时，你可以利用数据集的功能，例如序列化将传递到另一个进程，或写出 XML 文件的信息的能力。

## <a name="see-also"></a>请参阅
[数据集工具](../data-tools/dataset-tools-in-visual-studio.md)