---
title: "更改 DataContext 方法的返回类型不能撤消 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 28398032eb4c17916af4294e5ccab386040cf98e
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>对 DataContext 方法的返回类型的更改操作不能撤消
更改 DataContext 方法的返回类型的操作无法撤消。 要恢复为自动生成的类型，您必须将该项从服务器资源管理器/数据库资源管理器中再次拖动到 O/R Designer 上。 是否确实要更改返回类型？  
  
<xref:System.Data.Linq.DataContext> 方法的返回类型根据您在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中放置项的位置而不同。 如果直接将项放在现有实体类上，则将创建具有该实体类返回类型的 <xref:System.Data.Linq.DataContext> 方法。 如果将项放在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白区域，则将创建返回自动生成类型的 <xref:System.Data.Linq.DataContext> 方法。 在将 <xref:System.Data.Linq.DataContext> 方法添加到方法窗格后可以更改该方法的返回类型。 若要检查或更改的返回类型<xref:System.Data.Linq.DataContext>方法中，选择它，然后单击**返回类型**中的属性**属性**窗口。  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>更改 DataColumn 的返回类型  
  
-   单击 **“是”**。  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>退出消息框，不更改返回类型  
  
-   单击“否” 。  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>在更改返回类型后恢复为原始返回类型  
  
1.  在 <xref:System.Data.Linq.DataContext>上选择 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 方法，然后删除它。  
  
2.  查找中的项**服务器资源管理器/数据库资源管理器**和将其拖动到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
    这样做将创建具有原始默认返回类型的 <xref:System.Data.Linq.DataContext> 方法。  
  
## <a name="see-also"></a>请参阅
[O/R 设计器消息](../data-tools/o-r-designer-messages.md)  
[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)