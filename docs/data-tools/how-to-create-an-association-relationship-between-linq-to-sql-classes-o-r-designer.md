---
title: "如何：创建 LINQ to SQL 类之间的关联（关系）（O/R 设计器） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建 LINQ to SQL 类之间的关联（关系）（O/R 设计器）
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中实体类之间的关联类似于数据库中表之间的关系。可以使用**“关联编辑器”**对话框创建实体类之间的关联。  
  
 使用**“关联编辑器”**对话框创建关联时，必须选择父类和子类。父类是包含主键的实体类；子类是包含外键的实体类。例如，如果创建映射到 Northwind Customers 和 Orders 表的实体类，则 Customer 类将是父类，而 Order 类将是子类。  
  
> [!NOTE]
>  将表从**“服务器资源管理器”**\/**“数据库资源管理器”**拖动到[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)]（[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]）上时，将根据数据库中现有的外键关系自动创建关联。  
  
 创建关联后，当您在 O\/R 设计器中选择该关联时，**“属性”**窗口中将有一些可配置属性。（关联是用相关类之间的连线表示的。）下表提供对关联的属性的说明。  
  
|属性|说明|  
|--------|--------|  
|**基数**|控制关联是一对多关系还是一对一关系。|  
|**子属性**|指定是否在父类上创建一个属性，作为关联关系外键一方上的子记录的集合或对这些子记录的引用。例如，在 Customer 和 Order 之间的关联中，如果**“子属性”**设置为**“True”**，则将在父类上创建一个名为 Orders 的属性。|  
|**父属性**|子类上引用关联父类的属性。例如，在 Customer 和 Order 之间的关联中，在 Order 类上创建一个名为 Customer 的属性，用来引用与订单关联的客户。|  
|**参与属性**|显示关联属性，并提供一个**“省略号”**按钮 \(...\)，该按钮可重新打开**“关联编辑器”**对话框。|  
|**唯一**|指定外目标列是否具有唯一性约束。|  
  
### 创建实体类之间的关联  
  
1.  右击表示关联中的父类的实体类，指向**“添加”**，然后单击**关联**。  
  
2.  验证在**“关联编辑器”**对话框中是否选择了正确的**“父类”**。  
  
3.  选择组合框中的**“子类”**。  
  
4.  选择实现类之间的关联的**“关联属性”**。通常，这种关联对应于数据库中定义的外键关系。例如，在 Customers 和 Orders 关联中，**“关联属性”**是每个类的 CustomerID。  
  
5.  单击**“确定”**创建关联。  
  
## 请参阅  
 [O\/R 设计器概述](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [演练：创建 LINQ to SQL 类（O\/R 设计器）](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext 方法（O\/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)   
 [如何：表示主键](../Topic/How%20to:%20Represent%20Primary%20Keys.md)