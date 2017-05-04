---
title: "设计业务数据连接模型 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 设计模型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 设计模型"
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 设计业务数据连接模型
  您可以通过将实体和方法添加到模型文件来开发业务数据连接 \(BDC\) 服务的模型。  实体描述数据字段的集合。  例如，实体可以表示数据库中的表。  方法执行诸如添加、删除或更新实体所表示的数据等任务。  有关详细信息，请参阅[将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## 添加实体  
 您可通过将**“实体”**从 Visual Studio 的**“工具箱”**拖到或复制到 BDC 设计器上来添加实体。  有关详细信息，请参阅[如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 在类中定义实体的字段。  例如，您可能会将名为 `Address` 的字段添加到 `Customer` 类。  您可以向项目添加新类，也可以使用通过“对象关系设计器（O\/R 设计器）”等其他工具创建的现有类。  实体的名称与表示实体的类的名称不必匹配。  在模型中定义方法时将类与实体相关。  
  
## 添加方法  
 当用户查看、添加、更新或删除基于模型的列表或 Web 部件中的信息时，BDC 服务将调用模型中的方法。  您必须为用户可执行的每个任务将方法添加到模型。  通过从**“BDC 方法详细信息”**窗口中选择五个基本方法类型中的任意一种类型来创建方法。  下表描述了 BDC 模型的五个基本方法。  
  
|方法|说明|  
|--------|--------|  
|Finder|返回实体实例的集合。  在用户打开列表或 Web 部件时调用。  有关详细信息，请参阅[如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)。|  
|特定的 Finder|返回特定的实体实例。  在用户查看列表中特定项的详细信息时调用。  有关详细信息，请参阅[如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)。|  
|Creator|将新数据添加到实体的数据源。  当用户在基于模型的列表的功能区上选择**“新建项”**按钮时调用。  有关详细信息，请参阅[如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)。|  
|Updater|修改列表中的数据。  在用户更新列表中的信息时调用。  有关详细信息，请参阅[如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)。|  
|Deleter|移除数据。  在用户从列表中删除项时调用。  有关详细信息，请参阅[如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)。|  
  
## 定义方法参数  
 当您创建方法时，Visual Studio 将添加适合于该方法类型的输入和输出参数。  这些参数只是占位符。  大多数情况下，您必须修改这些参数以使它们传入或返回正确的数据类型。  例如，默认情况下，Finder 方法返回字符串。  大多数情况下，您需要修改 Finder 方法的返回参数以使其返回实体的集合。  可通过修改参数的类型描述符来实现这一点。  类型描述符是描述参数的数据类型的特性集合。  有关详细信息，请参阅[如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
 Visual Studio 使您能够在模型中的参数之间复制类型描述符。  例如，您可能会为 `GetCustomer` 方法的返回参数定义一个名为 `CustomerTD` 的类型描述符。  您可以在**“BDC 资源管理器”**中复制 `CustomerTD` 类型描述符，然后将该类型描述符粘贴到 `CreateCustomer` 方法的输入参数中。  这样，您将不必定义同一类型描述符多次。  
  
##  <a name="MethodInstances"></a> 方法实例  
 当您创建方法时，Visual Studio 会添加一个默认方法实例。  方法实例是对方法的引用，加上参数的默认值。  单个方法可以有多个方法实例。  每个实例都是方法签名和一组默认值的组合。  有关详细信息，请参阅[如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
 当您运行项目时，方法实例将出现在 SharePoint 列表上方的下拉列表中。  用户可以选择方法实例来查看数据。  
  
 若要向方法实例中添加默认值，您必须直接修改模型的 XML。  有关详细信息，请参阅[默认值](http://go.microsoft.com/fwlink/?LinkID=169279)。  
  
## 添加筛选器描述符  
 模型的使用者可能需要检索与某些条件匹配的实例。  为了实现此功能，您可以向方法中添加筛选器描述符。  利用筛选器描述符，模型使用者可以通过在方法执行之前将值传递到方法来筛选方法结果集。  有关更多信息，请参见 [How to: Add Filter Parameters to Operations to Limit Instances from the External System](http://go.microsoft.com/fwlink/?LinkID=169267)（如何：向操作中添加筛选器参数以限制来自外部系统的实例）。  
  
 SharePoint 提供了若干使用户能够提供筛选器值的功能。  例如，业务数据 Web 部件提供了筛选器文本框。  用户可通过在该文本框中键入值来限制列表中的数据。  有关如何向方法中添加筛选器描述符的更多信息，请参见[如何：向 Finder 方法中添加筛选器描述符](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。  
  
### 筛选器描述符属性  
 您必须设置筛选器描述符的**“关联的类型描述符”**、**“名称”**和**“类型”**属性。  所有其他属性可选。  
  
 **“关联的类型描述符”**属性将筛选器描述符与输入参数联系在一起。  当用户提供筛选器值时，BDC 服务将通过使用输入参数将该值传入方法。  
  
 **“类型”**属性描述要使用的筛选模式。  在 SharePoint 中，所选的筛选模式将影响用户界面 \(UI\) 中出现的文本。  例如，对于比较运算符筛选模式，文本**“等于”**将显示为业务数据 Web 部件上方的一个控件。  有关每种筛选模式的更多信息，请参见 [BDC 支持的筛选器的类型](http://go.microsoft.com/fwlink/?LinkId=169287)。  
  
 有关筛选器描述符属性的更多信息，请参见 [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280)。  
  
### 提供默认值  
 在某些情况下，用户可能未提供筛选器值。  可通过向方法实例中添加默认值或在方法的代码中设置默认值来提供默认值。  有关如何向方法实例中添加默认值的更多信息，请参见 [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  有关如何在方法代码中设置输入参数的默认值的示例，请参见[如何：向 Finder 方法中添加筛选器描述符](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。  
  
## 验证模型  
 可以在开发过程中验证模型。  Visual Studio 可标识使模型无法按预期方式工作的问题。  这些问题显示在 Visual Studio 的**“错误列表”**中。  
  
 通过打开 BDC 设计器的快捷菜单中选择 **验证 \(V\)**来验证模型。  如果模型包含任何错误，这些错误将出现在 **错误列表**中。  您可以通过双击错误快速将光标移至列表中包含错误的代码。  或者，您可以选择 F8 或 Shift\+F8 键在列表的错误中来回跳转。  
  
 如果违反了模型规则的某个方面，则会发生验证错误。  例如，如果类型描述符的**“IsCollection”**属性设置为 **true**，但子类型描述符不存在，则将出现验证错误。  您可能必须参考 BDC 模型的规则来了解出现在 Visual Studio 的**“错误列表”**中的某些错误。  有关 BDC 模型规则的更多信息，请参见 [BDCMetadata 架构](http://go.microsoft.com/fwlink/?LinkID=169275)。  
  
## 调试包含模型的解决方案  
 您可以调试代码，就像调试 Visual Studio 中的任何代码一样。  若要调试代码，请在代码中的任意位置设置断点，然后启动调试器。  Visual Studio 将打开 SharePoint 网站。  在 SharePoint 中，创建使用业务数据的列表或 Web 部件。  然后，您可以单步执行代码。  有关调试 SharePoint 项目的更多信息，请参见[SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
 也可以调试添加到项目中的自定义程序集中的代码。  但若要调试自定义程序集中的代码，您必须将程序集添加到解决方案包中。  有关详细信息，请参阅[如何：添加和移除附加程序集](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 有关如何向项目中添加自定义程序集的更多信息，请参见[如何：在 BDC 功能中引入自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)。  
  
### 配置 BDC 安全性  
 您可能必须修改 SharePoint 中的安全性设置，然后才能调试解决方案。  若要修改这些设置，请在 SharePoint 2010 管理中心网站中打开业务数据连接服务应用程序。  在**“设置元数据存储区权限”**对话框中添加您的用户帐户，然后选择以下任意选项：  
  
|任务|选项|  
|--------|--------|  
|将模型部署到 BDC 服务。|Edit|  
|通过使用模型中的外部内容类型（实体）创建列表和 Web 部件。|在客户端中可选|  
|创建、读取、更新和删除实体数据。|执行|  
  
 有关这些设置的更多信息，请参见 [业务数据连接服务管理](http://go.microsoft.com/fwlink/?LinkID=178883)。  
  
 您也可以为个别模型或外部内容类型设置安全权限。  有关如何设置模型的安全权限的更多信息，请参见 [BDC 模型控制](http://go.microsoft.com/fwlink/?LinkID=178884)。  有关如何设置外部内容类型的安全权限的更多信息，请参见[管理外部内容类型 \(SharePoint Server 2010\)](http://go.microsoft.com/fwlink/?LinkID=178885)。  
  
> [!NOTE]  
>  使用这些设置在本地 SharePoint 服务器上调试解决方案。  有关如何在生产 SharePoint 服务器上配置 BDC 相关安全性设置的更多信息，请参见 [Business Connectivity Services 安全性概述 \(SharePoint Server 2010\)](http://go.microsoft.com/fwlink/?LinkID=178886)。  
  
### 回收损坏的模型  
 当您第一次启动调试器时，Visual Studio 会将整个模型部署到 SharePoint。  之后每次启动调试器时，Visual Studio 都会用您在部署过程之间进行的任何更改更新 SharePoint 中的模型。  
  
 在某些情况下，您可能希望 Visual Studio 从 SharePoint 中完全回收模型。  举例而言，模型可能会损坏。若要将模型重新部署到 SharePoint，请将模型的 **“增量更新”**属性设置为**“False”**，然后启动调试器。  当您选择表示**“BDC 资源管理器”**中的模型的节点时，**“增量更新”**属性将出现在**“属性”**窗口中。  默认情况下，该模型的名称为**“BdcModel1”**。  
  
### 更改模型中实体的标识符名称  
 如果在部署模型后更改标识符名称，则可能会收到部署错误。  无法通过将模型的**“增量更新”**属性设置为**“False”**来纠正此错误。  必须手动收回模型，然后重新部署解决方案。  有关详细信息，请参阅[SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)。  可以通过在最初部署模型之前将**“增量更新”**属性设置为**“False”**来避免此错误。  
  
## 查找 BDC 模型元素的文档  
 Visual Studio 将为您创建的每个实体、方法或其他项向模型中添加 XML 元素。  元素特性显示为**“属性”**窗口中的属性。  有关 Visual Studio 在您设计模型时生成的元素和特性的信息，请参见 [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275)（BDCMetadata 架构）。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)|介绍可用于直观地为 BDC 设计模型的工具。|  
|[如何：向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)|演示如何向模型中添加外部内容类型或实体。|  
|[如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)|演示如何添加使用户能够查看列表或 Web 部件中的实体列表的方法。|  
|[如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)|演示如何添加使用户能够查看特定实体的详细信息的方法。|  
|[如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)|演示如何添加使用户能够直接从列表或 Web 部件向数据源中添加记录的方法。|  
|[如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)|演示如何添加使用户能够使用列表或 Web 部件的用户界面 \(UI\) 中的选项从数据源中移除数据的方法。|  
|[如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)|演示如何添加使用户能够直接从列表或 Web 部件更改数据源中的数据记录的方法。|  
|[如何：向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)|演示如何使用 Visual Studio 中的“方法详细信息”窗口向方法中添加输入和返回参数。|  
|[如何：定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|演示如何在模型中定义参数数据类型。|  
|[如何：定义方法实例](../sharepoint/how-to-define-a-method-instance.md)|演示如何创建 BDC 所执行的方法的实例。|  
|[如何：向 Finder 方法中添加筛选器描述符](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|演示如何使用户能够限制 Finder 方法返回的实例数。|  
|[创建实体之间的关联](../sharepoint/creating-an-association-between-entities.md)|介绍如何能够在模型中的实体之间定义关系。  业务数据 Web 部件、外部列表和自定义应用程序可在用户界面 \(UI\) 中显示这些数据关系。|  
|[如何：创建实体之间的关联](../sharepoint/how-to-create-an-association-between-entities.md)|演示如何在模型中的实体之间定义关系。|  
|[演练：使用业务数据在 SharePoint 中创建外部列表](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|提供一些分步说明，这些分步说明演示如何创建和测试一个在 SharePoint 外部列表中显示联系人的模型。|  
|[将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)|提供为 BDC 服务创建和设计模型的概述。|  
  
  