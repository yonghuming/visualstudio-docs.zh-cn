---
title: "如何：使用 MSBuild 目标自定义 SharePoint 解决方案包 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 开发, 包"
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：使用 MSBuild 目标自定义 SharePoint 解决方案包
  您可以使用命令提示符 MSBuild 目标来自定义 Visual Studio 创建 SharePoint 包文件 \(.wsp\) 的方式。  例如，您可以自定义用于改变指定打包的中间目录的 MSBuild 属性和用于指定枚举的文件的MSBuild 项组。  
  
## 自定义和运行 MSBuild 目标  
 如果自定义 BeforeLayout 和 AfterLayout 目标，您可以在布局包之前执行任务，例如，添加、移除或修改要打包的文件。  
  
#### 自定义 BeforeLayout 目标  
  
1.  打开编辑器，如"记事本"，然后添加以下代码。  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     目标打包之前，此示例显示消息。  
  
2.  将该文件命名为 **CustomLayout.SharePoint.targets**，然后将其保存在 SharePoint 项目中的文件夹。  
  
3.  打开项目，并打开其快捷菜单，然后选择 **卸载项目**。  
  
4.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“编辑** *ProjectName***.vbproj** 或者 **编辑** *ProjectName***.csproj**。  
  
5.  在临近项目文件末尾附近 \(的 `Import` 行后面，添加下列行。  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  保存并关闭项目文件。  
  
7.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“重载项目”**。  
  
 当您发布项目时，在打包开始之前，消息将显示输出。  
  
#### 自定义 AfterLayout 目标  
  
1.  在菜单栏上，依次选择**“文件”**、**“打开”**、**“文件”**。  
  
2.  在 **打开文件** 对话框，请导航到项目文件夹，选择 CustomLayout.target 文件，然后选择 **打开** 按钮。  
  
3.  在紧接 `</Project>` 标记的前方添加下列代码：  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     此目标打包后，此示例显示一条消息。  
  
4.  保存并关闭目标文件。  
  
5.  重新启动 Visual Studio，并打开项目。  
  
 在发布项目时，打包开始前显示BeforeLayout 消息，同时在打包完成之后，显示 AfterLayout 消息。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  