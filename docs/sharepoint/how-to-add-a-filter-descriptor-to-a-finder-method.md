---
title: "如何：向 Finder 方法中添加筛选器描述符"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], 添加筛选器"
  - "BDC [Visual Studio 中的 SharePoint 开发], 筛选器描述符"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 添加筛选器"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 筛选器描述符"
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：向 Finder 方法中添加筛选器描述符
  利用筛选器描述符，模型的使用者可以在方法执行之前将值传递到方法。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 一种常见方案是：SharePoint 中的用户希望检索与某个条件匹配的外部内容类型的实例。  可通过向 Finder 方法中添加筛选器描述符来支持此方案。  
  
### 向 Finder 方法中添加筛选器描述符  
  
1.  在**“BDC 方法详细信息”**窗口中，展开 Finder 方法的节点，展开**“参数”**节点，然后添加输入参数。  有关详细信息，请参阅[如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)。  
  
2.  在**“方法详细信息”**窗口中，选择参数的类型描述符。  
  
3.  在菜单栏上，选择**“视图”**，**“属性窗口”**。  
  
4.  在**“属性”**窗口中，将**“类型名称”**属性设置为适合于筛选器的数据类型。  
  
     例如，筛选器可能使用订单日期来限制方法返回的销售订单数。  若要支持该筛选器，类型描述符的**“类型名称”**属性必须设置为 **System.DateTime**。  
  
5.  在**“方法详细信息”**窗口中，展开**“筛选器描述符”**节点。  
  
6.  在 **添加筛选器描述符** 列表中，选择 **创建筛选器描述符**。  
  
     **“筛选器描述符”**节点下将出现一个新的筛选器描述符。  
  
7.  在菜单栏上，选择**“视图”**，**“属性窗口”**。  
  
8.  在**“属性”**窗口中，选择**“类型”**属性。  
  
9. 在**“类型”**属性显示的列表中，选择所需的筛选模式。  
  
     例如，若要创建使用订单日期来限制 Finder 方法中返回的销售订单数的筛选器，请选择**“Comparison”**。  比较筛选器确保 Finder 方法返回满足特定条件的实例。  有关每种筛选模式的更多信息，请参见 [BDC 支持的筛选器的类型](http://go.microsoft.com/fwlink/?LinkId=169287)。  
  
10. 在**“属性”**窗口中，选择**“关联的类型描述符”**属性。  
  
11. 在**“关联的类型描述符”**属性显示的列表中，选择您之前在此过程中创建的类型描述符。  这样会将筛选器与 Finder 方法的输入参数相关。  
  
12. 向 Finder 方法中添加返回数据的代码。  您可以使用输入参数作为 Select 查询中的条件。  
  
     下面的示例返回具有指定订单日期的销售订单。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#11](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#11)]  
  
## 请参阅  
 [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  