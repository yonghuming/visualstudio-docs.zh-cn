---
title: "如何：向方法添加参数"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 向参数添加方法"
  - "BDC [Visual Studio 中的 SharePoint 开发], 方法参数"
  - "BDC [Visual Studio 中的 SharePoint 开发], 参数"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 向参数添加方法"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 方法参数"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 参数"
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：向方法添加参数
  使用参数可将信息传递到方法或从方法返回信息。  所有方法必须至少有一个参数。  有关如何设计参数以支持要创建的方法类型的更多信息，请参见[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 将参数添加到方法时，Visual Studio 会将 `<Parameter>` 元素添加到项目中模型文件的 XML。  有关 `<Parameter>` 元素的特性的更多信息，请参见 [参数](http://go.microsoft.com/fwlink/?LinkId=169284)。  
  
### 向方法添加参数  
  
1.  向实体添加方法。  
  
2.  在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 方法详细信息**。  
  
     将打开**“BDC 方法详细信息”**窗口。  有关详细信息，请参阅[BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在**“BDC 方法详细信息”**窗口中，展开该方法的节点，然后展开**“参数”**节点。  
  
4.  在 **添加一个参数** 列表中，选择 **创建参数**。  
  
     一个新参数将显示在**“参数”**节点下方。  
  
5.  在菜单栏上，选择**“视图”**，**“属性窗口”**。  
  
6.  在**“属性”**窗口中，将**“名称”**属性设置为有意义的任何名称。  例如，如果该方法将返回客户，则可以将该方法命名为 GetCustomers。  
  
7.  在**“BDC 方法详细信息”**窗口中，打开所显示的参数方向列表，然后选择**“In”**、**“InOut”**、**“Out”**或**“Return”**。  
  
     有关在创建方法类型时要选择哪个方向的更多信息，请参见[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
8.  修改参数的类型描述符。  有关详细信息，请参阅[如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## 请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  