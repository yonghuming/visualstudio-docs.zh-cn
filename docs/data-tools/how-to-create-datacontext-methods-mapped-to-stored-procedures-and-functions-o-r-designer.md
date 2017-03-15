---
title: "如何：创建映射到存储过程和函数的 DataContext 方法（O/R 设计器） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建映射到存储过程和函数的 DataContext 方法（O/R 设计器）
存储过程和函数可作为 <xref:System.Data.Linq.DataContext> 方法添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中。调用该方法并传入所需参数将对数据库运行存储过程或函数，并返回 <xref:System.Data.Linq.DataContext> 方法的返回类型的数据。有关 <xref:System.Data.Linq.DataContext> 方法的详细信息，请参见 [DataContext 方法（O\/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
> [!NOTE]
>  将更改从实体类保存到数据库时，还可以使用存储过程重写执行插入、更新和删除操作的默认 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 运行时行为。有关更多信息，请参见[如何：分配存储过程以执行更新、插入和删除（O\/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## 创建 DataContext 方法  
 可以将存储过程或函数从**“服务器资源管理器\/数据库资源管理器”**拖动到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上来创建 <xref:System.Data.Linq.DataContext> 方法。  
  
> [!NOTE]
>  根据在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上放置存储过程或函数的位置不同，生成的 <xref:System.Data.Linq.DataContext> 方法的返回类型也有所不同。如果直接将项放在现有实体类上，则将创建具有该实体类返回类型的 <xref:System.Data.Linq.DataContext> 方法。如果将项放在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白区域，则将创建返回自动生成类型的 <xref:System.Data.Linq.DataContext> 方法。在将 <xref:System.Data.Linq.DataContext> 方法添加到方法窗格后可以更改该方法的返回类型。若要检查或更改 <xref:System.Data.Linq.DataContext> 方法的返回类型，请选中该方法并在**“属性”**窗口中检查**“返回类型”**属性。有关更多信息，请参见[如何：更改 DataContext 方法的返回类型（O\/R 设计器）](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 创建返回自动生成类型的 DataContext 方法  
  
1.  在**“服务器资源管理器”**\/**“数据库资源管理器”**中，展开正在使用的数据库的**“存储过程”**节点。  
  
2.  找到所需的存储过程并将其拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白区域。  
  
     具有自动生成返回类型的 <xref:System.Data.Linq.DataContext> 方法即被创建，并出现在**“方法”**窗格中。  
  
#### 创建具有实体类的返回类型的 DataContext 方法  
  
1.  在**“服务器资源管理器”**\/**“数据库资源管理器”**中，展开正在使用的数据库的**“存储过程”**节点。  
  
2.  找到所需的存储过程并将其拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的一个现有实体类上。  
  
     具有所选实体类的返回类型的 <xref:System.Data.Linq.DataContext> 方法即被创建，并出现在**“方法”**窗格中。  
  
> [!NOTE]
>  有关更改现有 <xref:System.Data.Linq.DataContext> 方法的返回类型的信息，请参见[如何：更改 DataContext 方法的返回类型（O\/R 设计器）](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
## 请参阅  
 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法（O\/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)   
 [演练：创建 LINQ to SQL 类（O\/R 设计器）](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Visual Basic 中的 LINQ 简介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [如何：在 C\# 中编写 LINQ 查询](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)