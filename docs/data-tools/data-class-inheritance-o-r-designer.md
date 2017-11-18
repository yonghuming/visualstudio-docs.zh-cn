---
title: "数据类继承 （O R 设计器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 13864f690af8b57cc23a218e20a098002e70a2ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="data-class-inheritance-or-designer"></a>数据类继承 （O/R 设计器）
像其他对象一样，[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 类可以使用继承，并可从其他类派生。 在代码中，可以通过声明一个类继承自另一个类来指定对象间的继承关系。 在数据库中，可通过多种方式创建继承关系。 [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)]（[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]）支持通常在关系系统中实现的单表继承概念。  
  
 在单表继承中，一个数据库表同时包含基类和派生类的列。 使用关系数据时，一个鉴别器列包含的值确定任意给定的记录属于哪个类。 例如，考虑一个包含公司所有员工的 Persons 表。 一些人是员工，一些人是经理。 Persons 表包含一个名为 Type 的列，该列用值 1 表示经理，用值 2 表示员工。 Type 列是鉴别器列。 在此方案中，可以创建一个员工子类，并仅使用 Type 值为 2 的记录来填充该类。  
  
 当配置实体类中的继承使用[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，将包含继承数据拖动到设计器两次的单个表拖动： 继承层次结构中每个类的一次。 将表格添加到设计器后，将其连接用继承项从**对象关系设计器**工具箱，然后在设置四个继承属性**属性**窗口。  
  
## <a name="inheritance-properties"></a>继承属性  
 下表列出了这些继承属性及其说明：  
  
|属性|描述|  
|--------------|-----------------|  
|鉴别器属性|决定当前记录所属的类的属性，该属性映射到列。|  
|基类鉴别器值|决定记录所属的基类的值，该值位于指定为鉴别器属性的列中。|  
|派生类鉴别器值|决定记录所属的派生类的值，该值位于指定为鉴别器属性的属性中。|  
|继承默认值|当属性中的值指定为时应填充的类**鉴别器属性**不匹配**基类鉴别器值**或**派生类鉴别器值**。|  
  
 创建一个使用继承并对应于关系数据的对象模型可能有些不易理解。 本主题提供了有关配置继承时所需的基本概念及各个属性的信息。 下列主题对如何使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]配置继承进行了更清楚的阐释。  
  
|主题|描述|  
|-----------|-----------------|  
|[如何： 通过使用 O/R 设计器配置继承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|描述如何使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]配置使用单表继承的实体类。|  
|[演练： 使用单表继承 （O/R 设计器） 创建 LINQ to SQL 类](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|提供有关如何使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]配置使用单表继承的实体类的分步说明。|  
  
## <a name="see-also"></a>另请参阅  
 [LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [演练： 创建 LINQ to SQL 类 （O R 设计器）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [演练： 使用单表继承 （O/R 设计器） 创建 LINQ to SQL 类](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [入门](/dotnet/framework/data/adonet/sql/linq/getting-started)