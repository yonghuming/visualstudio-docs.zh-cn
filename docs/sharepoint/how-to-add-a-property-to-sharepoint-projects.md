---
title: "How to: Add a Property to SharePoint Projects | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  可以使用项目扩展向任何 SharePoint 项目中添加属性。  在**“解决方案资源管理器”**中选择该属性时，该属性会出现在**“属性”**窗口中。  
  
 下面的步骤假定您已创建了一个项目扩展。  有关更多信息，请参见[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
### 向 SharePoint 项目中添加属性  
  
1.  定义一个具有公共属性的类，该公共属性表示要添加到 SharePoint 项目的属性。  若要添加多个属性，则可以在同一个类中定义所有属性，也可以在不同的类中定义所有属性。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 实现的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法中，处理 *projectService* 参数的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件。  
  
3.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件的事件处理程序中，将您的属性类的实例添加到事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> 集合中。  
  
## 示例  
 下面的代码示例演示如何将两个属性添加到 SharePoint 项目中。  其中，一个属性将其数据保留在项目用户选项文件（.csproj.user 文件或 .vbproj.user 文件）中。  另一个属性将其数据保留在项目文件（.csproj 文件或 .vbproj 文件）中保留。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### 了解代码  
 为了确保每当 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件发生时都使用 `CustomProjectProperties` 类的同一个实例，该代码示例在此事件第一次发生时，将属性对象添加到项目的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性中。  无论此事件什么时候再次发生，代码都将检索此对象。  有关使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性将数据与项目关联的更多信息，请参见[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 为了保留对属性值所做的更改，属性的 **set** 访问器将使用以下 API：  
  
-   `CustomUserFileProperty` 使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 属性将其值保存到项目用户选项文件中。  
  
-   `CustomProjectFileProperty` 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 方法将其值保存到项目文件中。  
  
 有关将数据保留在这些文件中的更多信息，请参见[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### 指定自定义属性的行为  
 通过将 <xref:System.ComponentModel> 命名空间中的特性应用于属性定义，可定义自定义属性在**“属性”**窗口中的显示方式和行为方式。  下列特性可用于多种方案：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>：指定属性在**“属性”**窗口中的显示名称。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>：指定选择属性时显示在**“属性”**窗口底部的描述字符串。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>：指定属性的默认值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>：指定**“属性”**窗口中显示的字符串与非字符串属性值之间的自定义转换。  
  
-   <xref:System.ComponentModel.EditorAttribute>：指定用于修改属性的自定义编辑器。  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  