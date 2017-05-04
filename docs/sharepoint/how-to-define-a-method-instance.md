---
title: "如何：定义方法实例 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 方法"
  - "BDC [Visual Studio 中的 SharePoint 开发], 方法实例"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 方法"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 方法实例"
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：定义方法实例
  必须至少为模型中的每个方法定义一个方法实例。  
  
 可以使用**“BDC 方法详细信息”**窗口添加方法实例。  添加方法实例时，Visual Studio 会将 `<MethodInstance>` 元素添加到项目中模型文件的 XML。  有关 `<MethodInstance>` 元素的特性的更多信息，请参见 [实例方法](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
### 定义方法实例  
  
1.  在**“BDC 方法详细信息”**窗口中，展开方法的节点，然后展开**“实例”**节点。  
  
2.  在**“添加实例方法”**下拉列表中，选择**“创建 Finder 实例”**。  
  
     **“实例”**节点下将显示新方法实例。  
  
3.  在菜单栏上，选择**“视图”**，选择**“属性窗口”**。  
  
4.  在**“属性”**窗口中，设置方法实例的属性。  有关每个属性的更多信息，请参见[实例方法](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
## 请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  