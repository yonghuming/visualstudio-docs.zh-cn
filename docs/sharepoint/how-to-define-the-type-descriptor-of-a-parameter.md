---
title: "如何：定义参数的类型描述符 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 参数类型"
  - "BDC [Visual Studio 中的 SharePoint 开发], 类型描述符"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 参数类型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 类型描述符"
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# 如何：定义参数的类型描述符
  类型描述符包含描述参数的数据类型的属性。  可以定义字段、实体或实体集合的类型描述符。  有关详细信息，请参阅 [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### 定义参数的类型描述符  
  
1.  在“BDC 方法详细信息”窗口中，选择该参数的类型描述符。  
  
2.  在菜单栏上，依次选择“视图”、“属性窗口”。  
  
3.  在“属性”窗口中，设置类型描述符的属性。  
  
     以下过程介绍如何将类型描述符定义为字段、实体或实体集合。  
  
### 定义字段  
  
1.  在“属性”窗口中，将类型描述符的“名称”属性设置为表示实体的类型中字段的名称（例如 FirstName）。  
  
2.  在“TypeName”属性旁边的列表中，选择适当的数据类型（例如“Int32”）。  
  
     有关其他可选参数的信息，请参阅 [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### 定义实体  
  
1.  在“属性”窗口中，将“名称”属性设置为描述实体的名称（例如联系人）。  
  
2.  将“TypeName”属性设置为表示实体的类型的完全限定名。  此类型可以是你的项目中的类，在你的解决方案中引用的程序集中定义的类型，或 BDC 对象模型中定义的类型。  
  
    -   对于你项目中的类，选择向下箭头旁边的“TypeName”属性，在出现的对话框中选择“当前项目”选项卡，然后选择你项目中的类。  
  
         完全限定名包括后跟 LOB 系统名称的命名空间和类名称。  以下示例将“TypeName”属性的值设置为你项目中的类。  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   对于你的解决方案中的程序集的类型，完全限定名包括类型名称、程序集名称、版本号、区域性和公钥标记。  
  
         以下示例将“TypeName”属性的值设置为在你的解决方案中引用的程序集中定义的类型。  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   对于 BDC 对象模型中定义的类型，完全限定名包括命名空间和类型名称。  
  
         以下示例将“TypeName”属性的值设置为 BDC 对象模型中的类型。  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  在“BDC 方法详细信息”窗口中，打开为类型描述符显示的列表，然后选择“编辑”。  
  
     将打开“BDC 资源管理器”窗口。  
  
4.  在“BDC 资源管理器”中，打开类型描述符的快捷菜单，然后选择“添加类型描述符”。  
  
     新的类型描述符将作为子类型描述符添加到实体类型描述符中。  将此类型描述符配置为字段。  
  
5.  重复步骤 4，为实体的每个字段添加子类型描述符。  
  
### 定义实体的集合  
  
1.  在“BDC 方法详细信息”窗口中，选择所需参数的类型描述符。  
  
2.  在菜单栏上，依次选择“视图”、“属性窗口”。  
  
3.  在“属性”窗口中，将“名称”属性设置为描述实体的名称（例如联系人）。  
  
4.  将“IsCollection”属性设置为 **True**。  这表示此类型描述符是实体的集合。  
  
5.  将“TypeName”属性设置为一个字符串，其中包含对 <xref:System.Collections.Generic.IEnumerable%601> 接口以及表示实体的类型的完全限定名的引用。  此类型可以是你的项目中的类，在你的解决方案中引用的程序集中定义的类型，或 BDC 对象模型中定义的类型。  
  
    -   对于你项目中的类，选择向下箭头旁边的“TypeName”属性，在出现的对话框中选择“当前项目”选项卡，然后选择你项目中的类。  
  
         完全限定名包括后跟 LOB 系统名称的命名空间和类名称。  
  
         以下示例将“TypeName”属性的值设置为你项目中的类集合。  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` `BdcModel1.Contact, BdcModel1]`  
  
    -   对于你的解决方案中的程序集的类型，完全限定名包括类型名称、程序集名称、版本号、区域性和公钥标记。  
  
         以下示例将“TypeName”属性的值设置为在你的解决方案中引用的程序集中的类型集合。  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`  
  
    -   对于 BDC 对象模型中定义的类型，完全限定名仅包括命名空间和类型名称。  
  
         以下示例将“TypeName”属性的值设置为 BDC 对象模型中定义的类型集合。  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`  
  
6.  在“BDC 方法详细信息”窗口中，打开为类型描述符显示的列表，然后选择“编辑”。  
  
     将打开“BDC 资源管理器”窗口。  
  
7.  在“BDC 资源管理器”中，打开类型描述符的快捷菜单，然后选择“添加类型描述符”。  
  
     新的类型描述符将作为子类型描述符添加到集合类型描述符中。  将此类型描述符配置为实体。  
  
## 请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  