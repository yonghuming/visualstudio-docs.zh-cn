---
title: "Extending SharePoint Project Items"
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
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  当您希望向 Visual Studio 中已安装的某个类型的 SharePoint 项目项添加功能时，请创建项目项扩展。  例如，您可以为 Visual Studio 中内置的**“事件接收器”**或**“列表定义”**项目项创建扩展，也可以为自定义项目项类型创建扩展。  您还可以为所有类型的 SharePoint 项目项创建扩展。  
  
## 用于扩展 SharePoint 项目项的任务  
 若要扩展项目项，请生成实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 接口的 Visual Studio 扩展程序集。  有关更多信息，请参见[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
 在扩展项目项时，还可以向项目项中添加以下功能：  
  
-   向项目项中添加快捷菜单项。  菜单项会在您打开项目项的快捷菜单在 **解决方案资源管理器**。  您打开快捷菜单通过右击项目项或通过选择然后选择 SHIFT \+ F10 键。  有关更多信息，请参见[How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)。  
  
-   向项目项中添加自定义属性。  当您在中选择 **解决方案资源管理器**时，的项目项属性出现在 **属性** 窗口。  有关更多信息，请参见[How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)。  
  
 有关演示如何创建、部署和测试项目项扩展的演练，请参见[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)。  
  
## 了解项目项扩展与项目项实例之间的关系  
 如果创建了项目项扩展，则在向 SharePoint 项目中添加关联类型的项目项时，Visual Studio 会加载您的扩展。  例如，如果您为**“事件接收器”**项目项创建了扩展，则 Visual Studio 会在用户向项目中添加**“事件接收器”**项目项时加载您的扩展。  Visual Studio 会将扩展的同一个实例用于关联项目项类型的所有实例。  在前面的示例中，如果用户向项目中添加另一个**“事件接收器”**项目项，则会使用同一个扩展实例来自定义第二个项目项。  
  
 若要访问要扩展的项目项类型的特定实例，请在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法的实现中处理 *projectItemType* 参数的一个 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件。  例如，若要确定所扩展类型的项目项添加到项目中的时间，请处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 事件。  有关更多信息，请参见[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
## SharePoint 项目项的标识符  
 每个 SharePoint 项目项均有对应的字符串标识符。  若要执行下列任务，您必须知道项目项的标识符：  
  
-   为项目项创建扩展。  在此情况下，您必须将要扩展的项目项的标识符传递给 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的构造函数。  若要为所有项目项类型创建扩展，请传递 **\*** 字符串值。  
  
-   以编程方式向项目中添加项目项。  在此情况下，您必须将项目项的标识符传递给 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> 方法。  
  
 下表列出了 Visual Studio 附带的 SharePoint 项目项的标识符。  
  
|项目项名称|字符串标识符|  
|-----------|------------|  
|业务数据目录模型|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|内容类型|Microsoft.VisualStudio.SharePoint.ContentType|  
|事件接收器|Microsoft.VisualStudio.SharePoint.EventHandler|  
|空元素|Microsoft.VisualStudio.SharePoint.GenericElement|  
|列表定义<br /><br /> 来自内容类型的列表定义|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|列表实例|Microsoft.VisualStudio.SharePoint.ListInstance|  
|模块|Microsoft.VisualStudio.SharePoint.Module|  
|顺序工作流<br /><br /> 状态机工作流|Microsoft.VisualStudio.SharePoint.Workflow|  
|网站定义|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|可视 Web 部件|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web 部件|Microsoft.VisualStudio.SharePoint.WebPart|  
|工作流关联窗体|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## 请参阅  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  