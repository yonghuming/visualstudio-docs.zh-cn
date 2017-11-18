---
title: "如何： 扩展 O R 设计器所生成的代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: cc60c4fe5ff014b1088509c8e5c4982bf7f4322a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>如何：扩展 O/R 设计器生成的代码
在更改设计器图面上的实体类和其他对象时，将重新生成由 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]生成的代码。 当设计器重新生成代码时，您添加到生成的代码中的任何代码一般都会被重新声称的代码覆盖。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供了一种生成分部类文件的功能，您可以将代码添加到分部类文件中而不会被覆盖。 将您自己的代码添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]生成的代码中的一个示例是在 LINQ to SQL（实体）类中添加数据验证。 有关信息，请参阅[如何： 向实体类添加验证](../data-tools/how-to-add-validation-to-entity-classes.md)。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>向实体类中添加代码  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>创建分部类并向实体类中添加代码  
  
1.  打开或创建一个新的 LINQ to SQL 类文件 (**.dbml**文件) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (双击**.dbml**文件中**解决方案资源管理器**/**数据库资源管理器**。)  
  
2.  在[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，右键单击你想要添加验证，然后单击的类**查看代码**。  
  
     将打开代码编辑器，其中显示所选实体类的分部类。  
  
3.  在该实体类的分部类声明中添加您的代码。  
  
## <a name="adding-code-to-a-datacontext"></a>向 DataContext 中添加代码  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>创建分部类并向 DataContext 中添加代码  
  
1.  打开或创建一个新的 LINQ to SQL 类文件 (**.dbml**文件) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (双击**.dbml**文件中**解决方案资源管理器**/**数据库资源管理器**。)  
  
2.  在[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，右键单击设计器上的空白区域，然后单击**查看代码**。  
  
     将打开代码编辑器，其中显示 DataContext 的分部类。  
  
3.  在 DataContext 的分部类声明中添加你的代码。  
  
## <a name="see-also"></a>另请参阅  
 [LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [演练： 创建 LINQ to SQL 类 （O R 设计器）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 