---
title: "如何：打开和关闭复数形式（O/R 设计器） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：打开和关闭复数形式（O/R 设计器）
默认情况下，将名称以 s 或 ies 结尾的数据库对象从**“服务器资源管理器”**\/**“数据库资源管理器”**拖放到 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)上时，生成的实体类的名称从复数形式变为单数形式。这样可以更准确地表示实例化的实体类映射到单个数据记录的事实。例如，将 Customers 表添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]将声称名为 Customer 的实体类，因为该类将仅为一个客户保存数据。  
  
> [!NOTE]
>  默认情况下，复数形式仅在 Visual Studio 的英语版本中启用。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 打开和关闭复数形式  
  
1.  在**“工具”**菜单上单击**“选项”**。  
  
2.  在**“选项”**对话框中展开**“数据库工具”**。  
  
> [!NOTE]
>  如果**“数据库工具”**节点不可见，请选择**“显示所有设置”**。  
  
1.  单击**“O\/R 设计器”**。  
  
2.  将**“名称的复数形式”**设置为**“启用”**\=**“False”**，可将 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]设置为不更改类名称。  
  
3.  将**“名称的复数形式”**设置为**“启用”**\=**“True”**，可向添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的对象的类名称应用复数规则。  
  
## 请参阅  
 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)