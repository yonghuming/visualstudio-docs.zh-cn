---
title: "如何： 定义参数的类型描述符 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19722a4cffb0e3708939734253b0f2c4a408389e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>如何：定义参数的类型描述符
  类型描述符包含描述参数的数据类型的属性。 可以定义字段、实体或实体集合的类型描述符。 有关详细信息，请参阅[TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>定义参数的类型描述符  
  
1.  在**BDC 方法详细信息**窗口中，选择参数的类型描述符。  
  
2.  在菜单栏上，选择**视图**，**属性窗口**。  
  
3.  在**属性**窗口中，设置类型描述符的属性。  
  
     以下过程介绍如何将类型描述符定义为字段、实体或实体集合。  
  
### <a name="to-define-a-field"></a>定义字段  
  
1.  在**属性**窗口中，设置**名称**为表示实体的类型中的字段的名称的类型描述符的属性 (例如： **FirstName**)。  
  
2.  在列表中下一步**TypeName**属性，选择适当的数据类型 (例如， **Int32**)。  
  
     有关其他可选参数的信息，请参阅[TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### <a name="to-define-an-entity"></a>定义实体  
  
1.  在**属性**窗口中，设置**名称**属性设置为描述实体的名称 (例如：**联系人**)。  
  
2.  设置**TypeName**为表示实体的类型的完全限定名称的属性。 此类型可以是你的项目中的类，在你的解决方案中引用的程序集中定义的类型，或 BDC 对象模型中定义的类型。  
  
    -   对于你的项目中的类，选择向下箭头旁边**TypeName**属性，选择**当前项目**对话框出现时，，然后选择您项目中的类中选项卡。  
  
         完全限定名包括后跟 LOB 系统名称的命名空间和类名称。 下面的示例设置的值**TypeName**到你的项目中的类的属性。  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   对于你的解决方案中的程序集的类型，完全限定名包括类型名称、程序集名称、版本号、区域性和公钥标记。  
  
         下面的示例设置的值**TypeName**在你的解决方案中引用的程序集中定义的类型的属性。  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   对于 BDC 对象模型中定义的类型，完全限定名包括命名空间和类型名称。  
  
         下面的示例设置的值**TypeName**属性设置为 BDC 对象模型中的类型。  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  在**BDC 方法详细信息**窗口中，打开类型描述符显示的列表，然后选择**编辑**。  
  
     **BDC 资源管理器**窗口随即打开。  
  
4.  在**BDC 资源管理器**，打开类型描述符的快捷菜单，然后选择**添加类型描述符**。  
  
     新的类型描述符将作为子类型描述符添加到实体类型描述符中。 将此类型描述符配置为字段。  
  
5.  重复步骤 4，为实体的每个字段添加子类型描述符。  
  
### <a name="to-define-a-collection-of-entities"></a>定义实体的集合  
  
1.  在**BDC 方法详细信息**窗口中，选择所需的参数的类型描述符。  
  
2.  在菜单栏上，选择**视图**，**属性窗口**。  
  
3.  在**属性**窗口中，设置**名称**属性设置为描述实体的名称 (例如：**联系人**)。  
  
4.  设置**IsCollection**属性**True**。 这表示此类型描述符是实体的集合。  
  
5.  设置**TypeName**属性设置为一个字符串，包含对引用<xref:System.Collections.Generic.IEnumerable%601>接口，并且表示实体类型的完全限定的名称。 此类型可以是你的项目中的类，在你的解决方案中引用的程序集中定义的类型，或 BDC 对象模型中定义的类型。  
  
    -   对于你的项目中的类，选择向下箭头旁边**TypeName**属性，选择**当前项目**对话框出现时，，然后选择您项目中的类中选项卡。  
  
         完全限定名包括后跟 LOB 系统名称的命名空间和类名称。  
  
         下面的示例设置的值**TypeName**到你的项目中的类集合的属性。  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace。` `BdcModel1.Contact，BdcModel1]  
  
    -   对于你的解决方案中的程序集的类型，完全限定名包括类型名称、程序集名称、版本号、区域性和公钥标记。  
  
         下面的示例设置的值**TypeName**属性设置为在你的解决方案中引用程序集中的类型的集合。  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact、 myAssemblyName，版本 = 4.0.0.0，Culture = neutral，PublicKeyToken = b77a5c561934e089]  
  
    -   对于 BDC 对象模型中定义的类型，完全限定名仅包括命名空间和类型名称。  
  
         下面的示例设置的值**TypeName**属性设置为 BDC 对象模型中定义的类型的集合。  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]  
  
6.  在**BDC 方法详细信息**窗口中，打开类型描述符显示的列表，然后选择**编辑**。  
  
     **BDC 资源管理器**窗口随即打开。  
  
7.  在**BDC 资源管理器**，打开类型描述符的快捷菜单，然后选择**添加类型描述符**。  
  
     新的类型描述符将作为子类型描述符添加到集合类型描述符中。 将此类型描述符配置为实体。  
  
## <a name="see-also"></a>另请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何： 向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定义方法实例](../sharepoint/how-to-define-a-method-instance.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  