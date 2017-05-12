---
title: "How to: Add a Property to a SharePoint Project Item Extension"
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
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  可以使用项目项扩展向 Visual Studio 中已安装的任何 SharePoint 项目项添加属性。  当在**“解决方案资源管理器”**中选择项目项时，该属性将出现在**“属性”**窗口中。  
  
 下面的步骤假定您已创建了一个项目项扩展。  有关更多信息，请参见[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### 向项目项扩展中添加属性  
  
1.  定义包含一个公共属性的类，该公共属性表示要添加到项目项类型的属性。  如果要将多个属性添加到一个项目项类型，则可以在同一个类中定义所有属性，也可以在不同的类中定义所有属性。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 实现的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法中，处理 *projectItemType* 参数的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 事件。  
  
3.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 事件的事件处理程序中，将您的属性类的实例添加到事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> 集合中。  
  
## 示例  
 下面的代码示例演示如何将一个名为**“Example Property”（示例属性）**的属性添加到“事件接收器”项目项。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### 了解代码  
 为了确保每当 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 事件发生时都使用 `CustomProperties` 类的同一个实例，该代码示例在此事件第一次发生时，将属性对象添加到项目项的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性。  无论此事件什么时候再次发生，代码都将检索此对象。  有关使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性将数据与项目项关联的更多信息，请参见[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 为了保持对属性值的更改，`ExampleProperty` 的 **set** 访问器会将新值保存到与该属性关联的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 对象的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 属性中。  有关使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 属性将数据与项目项保存在一起的更多信息，请参见[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### 指定自定义属性的行为  
 通过将 <xref:System.ComponentModel> 命名空间中的特性应用于属性定义，可定义自定义属性在**“属性”**窗口中的显示方式和行为方式。  下列特性可用于多种方案：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>：指定属性在**“属性”**窗口中的显示名称。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>：指定选择属性时显示在**“属性”**窗口底部的描述字符串。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>：指定属性的默认值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>：指定**“属性”**窗口中显示的字符串与非字符串属性值之间的自定义转换。  
  
-   <xref:System.ComponentModel.EditorAttribute>：指定用于修改属性的自定义编辑器。  
  
## 编译代码  
 这些示例需要引用了下列程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  