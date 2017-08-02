---
title: "如何：将控件标记为安全控件"
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
  - "安全控件 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 高级打包工具"
  - "Visual Studio 中的 SharePoint 开发, 安全控件"
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：将控件标记为安全控件
  为了安全起见，SharePoint 对可防止脚本注入的 Web 控件和未防止脚本注入的 Web 控件进行了区分。  不受信任的用户可以访问受保护的控件（或安全控件）。  您可以在 SharePoint 项目项的“安全控制项”属性中将控件标记为安全，或在向包中添加程序集时在**“包设计器”**中将控件标记为安全。  有关更多信息，请参见  
  
 [web.config 文件设置更改](http://go.microsoft.com/fwlink/?LinkId=178965) 和 [注册 Web 部件程序集作为一个安全控件](http://go.microsoft.com/fwlink/?LinkId=171013)。  
  
> [!IMPORTANT]  
>  这些过程用于阐释目的。  只有在确信控件安全时才将控件标记为安全。  
  
## 在“安全控制项”属性中标记安全控件  
  
#### 在“安全控制项”属性中将控件标记为安全或不安全  
  
1.  创建包含可视 Web 部件项目的 SharePoint 解决方案。  
  
2.  向 Web 部件中添加两个控件：一个文本框和一个按钮。  分别保留名称的默认值 TextBox1 和 Button1。  
  
3.  向 Web 部件的**“安全控制项”**属性中添加两项。  为此，请选择**“属性”**窗口中**“安全控制项”**属性旁边的省略号 \(![ASP.NET 移动设计器中的省略号](~/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\) 按钮。  
  
     将出现**“安全控制项”**对话框。  
  
4.  在**“安全控制项”**对话框中，选择**“添加”**按钮两次，向**“成员”**窗格中添加两个安全控件项：一个用于按钮，一个用于文本框。  
  
5.  选择第一个安全控件项，并将其**“安全”**属性的值更改为**“False”**，将其**“类型名称”**属性更改为**“Button1”**，并将其**“安全应对脚本”**属性更改为**“False”**。  
  
     此步骤将按钮控件标识为不安全控件。  
  
6.  选择列表中的第二个安全控件项。  将其**“安全”**属性的值保留为**“True”**，将其**“类型名称”**属性设置为**“TextBox1”**，并将其**“安全应对脚本”**属性设置为**“True”**。  
  
     文本框控件现在即标记为可安全应对脚本注入的控件。  
  
7.  选择**“确定”**按钮以关闭对话框。  
  
## 在包设计器中标记安全控件  
  
#### 在包设计器中将控件标记为安全或不安全  
  
1.  创建包含可视 Web 部件项目的 SharePoint 解决方案。  
  
2.  向 Web 部件中添加两个控件：一个文本框和一个按钮。  分别保留名称的默认值 TextBox1 和 Button1。  
  
     记下控件的命名空间，因为稍后将用到该命名空间。  
  
3.  在菜单栏上，选择**“生成”**，**“生成解决方案”**生成项目。  
  
4.  创建另一个 SharePoint 解决方案。  
  
5.  在 **解决方案资源管理器**中，打开 Package.package 文件的快捷菜单，然后选择 **打开** 打开 **包设计器**。  
  
6.  在**“包设计器”**中，选择**“高级”**选项卡。  
  
7.  在**“其他程序集”**下，选择**“添加”**按钮，然后从列表中选择**“添加现有程序集”**。  
  
8.  在**“添加现有程序集”**对话框中，选择**“源文件路径”**旁边的省略号 \(![ASP.NET 移动设计器中的省略号](~/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\) 按钮。  
  
9. 从您在步骤 1 中创建的 SharePoint 解决方案选择程序集，然后选择 **打开** 按钮。  
  
10. 对于此示例，请将**“部署目标”**选项保留为 GlobalAssemblyCache。  
  
     此步骤将使程序集部署到系统全局程序集缓存 \(GAC\)。  如果希望程序集部署到 Web 应用程序 \(Bin\) 文件夹，请改为选择该选项。  有关更多信息，请参见 [在 SharePoint Foundation 中部署的 Web 部件](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
11. 在**“安全控件”**框中，选择**“单击此处添加新项”**按钮。  
  
12. 依据下表输入属性的值。  
  
    |属性名|值|  
    |---------|-------|  
    |命名空间|控件的完全限定命名空间，例如 **BdcModelProject1.VisualWebPart1**。|  
    |类型名称|Button1|  
    |程序集名称|程序集强名称，例如：Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c。|  
    |安全|清除**“安全”**复选框。|  
    |安全应对脚本|保留**“安全应对脚本”**复选框为清除状态。|  
  
    > [!NOTE]  
    >  通过**“包设计器”**的**“高级”**选项卡添加的程序集的**“程序集名称”**值不能为标记，它必须为强名称的程序集。  有关更多信息，请参见[创建和使用具有强名称的程序集](http://go.microsoft.com/fwlink/?LinkId=177513)。  
  
13. 选择标记为键创建另一个安全控件项。  
  
14. 再次选择**“单击此处添加新项”**按钮。  
  
15. 依据下表输入属性的值。  
  
    |属性名|值|  
    |---------|-------|  
    |命名空间|控件的完全限定命名空间，例如 **BdcModelProject1.VisualWebPart1**。|  
    |类型名称|TextBox1|  
    |程序集名称|程序集强名称，例如：Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c。|  
    |安全|选中**“安全”**复选框。|  
    |安全应对脚本|选中**“安全应对脚本”**复选框。|  
  
16. 选择标记为键，然后选择 **确定** 按钮关闭对话框。  
  
## 请参阅  
 [在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  