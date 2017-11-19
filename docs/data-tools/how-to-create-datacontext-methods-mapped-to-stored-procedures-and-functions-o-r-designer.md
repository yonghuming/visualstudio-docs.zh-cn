---
title: "如何： 创建映射到存储的过程和函数 （O R 设计器） 的 DataContext 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: a162c9cb7cf7febf6e3b6e95e927a31b6591b027
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>如何： 创建映射到存储的过程和函数 （O/R 设计器） 的 DataContext 方法
存储的过程和函数可以添加到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]作为<xref:System.Data.Linq.DataContext>方法。 调用该方法并传入所需参数将对数据库运行存储过程或函数，并返回 <xref:System.Data.Linq.DataContext> 方法的返回类型的数据。 有关详细信息<xref:System.Data.Linq.DataContext>方法，请参阅[DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
> [!NOTE]
>  将更改从实体类保存到数据库时，还可以使用存储过程重写执行插入、更新和删除操作的默认 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 运行时行为。 有关详细信息，请参阅[如何： 分配存储的过程以便执行更新、 插入和删除操作 （O/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## <a name="creating-datacontext-methods"></a>创建 DataContext 方法  
 你可以创建<xref:System.Data.Linq.DataContext>方法通过拖动存储过程或函数从**服务器资源管理器/数据库资源管理器**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
> [!NOTE]
>  根据在 <xref:System.Data.Linq.DataContext>上放置存储过程或函数的位置不同，生成的 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 方法的返回类型也有所不同。 如果直接将项放在现有实体类上，则将创建具有该实体类返回类型的 <xref:System.Data.Linq.DataContext> 方法。 如果将项放在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白区域，则将创建返回自动生成类型的 <xref:System.Data.Linq.DataContext> 方法。 在将 <xref:System.Data.Linq.DataContext> 方法添加到方法窗格后可以更改该方法的返回类型。 若要检查或更改的返回类型<xref:System.Data.Linq.DataContext>方法中，选择它，然后检查**返回类型**中的属性**属性**窗口。 有关详细信息，请参阅[如何： 更改 DataContext 方法 （O/R 设计器） 的返回类型](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>创建返回自动生成类型的 DataContext 方法  
  
1.  在**服务器资源管理器**/**数据库资源管理器**，展开**存储过程**你正在使用的数据库的节点。  
  
2.  找到所需的存储过程并将其拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白区域。  
  
     <xref:System.Data.Linq.DataContext>方法创建具有自动生成的返回类型，并出现在**方法**窗格。  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>创建具有实体类的返回类型的 DataContext 方法  
  
1.  在**服务器资源管理器**/**数据库资源管理器**，展开**存储过程**你正在使用的数据库的节点。  
  
2.  找到所需的存储过程并将其拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的一个现有实体类上。  
  
     <xref:System.Data.Linq.DataContext>方法创建具有所选的实体类返回类型，并出现在**方法**窗格。  
  
> [!NOTE]
>  有关更改现有的返回类型信息<xref:System.Data.Linq.DataContext>方法，请参阅[如何： 更改 DataContext 方法 （O/R 设计器） 的返回类型](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
## <a name="see-also"></a>另请参阅  
 [LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)   
 [演练： 创建 LINQ to SQL 类](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Visual Basic 中的 LINQ 简介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [如何：在 C# 中编写 LINQ 查询](http://msdn.microsoft.com/Library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)