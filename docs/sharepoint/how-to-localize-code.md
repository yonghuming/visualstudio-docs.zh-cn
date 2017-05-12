---
title: "如何：本地化代码"
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
  - "本地化代码 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 本地化"
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：本地化代码
  未本地化的代码使用硬编码的字符串值。  若要本地化代码字符串，请将它们替换为对 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 的调用，该方法是一种引用本地化资源的方法。  
  
## 本地化代码  
  
#### 本地化代码  
  
1.  在**“解决方案资源管理器”**中，开启工程项的快捷菜单，然后选择**添加“模块”**。  
  
     选择 **资源文件** 模板。  
  
    > [!NOTE]  
    >  确保将资源文件添加到 SharePoint 项目项，以便“部署类型”属性可用。  本过程后面需要此属性。  
  
2.  为默认语言资源文件指定一个附带有 .resx 扩展名的所选名称，例如 MyAppResources.resx。  
  
3.  重复1和2步骤，向 SharePoint 项目项中添加单独的资源文件：每种本地化语言各对应一个文件。  
  
     为每个本地化资源文件使用同一基名称，但添加区域性 ID。  例如，将德语本地化资源命名为 MyAppResources.de\-DE.resx。  
  
4.  打开每个资源文件并添加本地化的字符串。  在每个文件中使用相同的字符串 。  
  
5.  将每个资源文件的**“部署类型”**属性的值更改为**“AppGlobalResource”**，使每个文件都部署到服务器的 App\_GlobalResources 文件夹。  
  
6.  将每个文件的**“生成操作”**属性的值保留为**“嵌入的资源”**。  
  
     嵌入的资源将编译到项目的DLL中。  
  
7.  生成项目以创建资源附属 DLL。  
  
8.  在**“包设计器”**中，选择**“高级”**选项卡并添加附属程序集。  
  
9. 在**“位置”**框中“位置”路径的前面添加区域性 ID 文件夹，例如 de\-DE\\*项目项名称Project Item Name*.resources.dll。  
  
10. 如果您的解决方案尚未引用 System.Web 程序集，请添加对该程序集的引用，并将代码中的指令添加到 <xref:System.Web>。  
  
11. 在您的代码中找到用户可见的所有硬编码的字符串，如 UI 文本、错误和消息文本。  使用以下语法，通过调用替换为 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法：  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. 选择 F5 键生成并运行项目。  
  
13. 在 SharePoint 中，更改默认显示语言。  
  
     本地化的字符串将出现在应用程序中。  若要显示本地化资源，SharePoint 服务器必须安装了与该资源文件的区域特点相匹配的语言包。  
  
## 请参阅  
 [本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何：本地化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何：本地化 ASPX 标记](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：添加资源文件](../sharepoint/how-to-add-a-resource-file.md)  
  
  