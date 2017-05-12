---
title: "在项目项中提供打包和部署信息"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SafeControlEntries"
  - "VS.SharePointTools.Project.ProjectOutputReference"
  - "VS.SharePointTools.Project.FeatureProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "功能属性 [Visual Studio 中的 SharePoint 开发]"
  - "功能接收器 [Visual Studio 中的 SharePoint 开发]"
  - "项目输出引用 [Visual Studio 中的 SharePoint 开发]"
  - "安全控件 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 高级打包工具"
  - "Visual Studio 中的 SharePoint 开发, 功能属性"
  - "Visual Studio 中的 SharePoint 开发, 功能接收器"
  - "Visual Studio 中的 SharePoint 开发, 项目输出引用"
  - "Visual Studio 中的 SharePoint 开发, 安全控件"
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 在项目项中提供打包和部署信息
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的所有 SharePoint 项目项都具有属性，您可以使用这些属性在将项目部署到 SharePoint 时提供附加数据。  这些属性如下所示：  
  
-   功能属性  
  
-   功能接收器  
  
-   项目输出引用  
  
-   安全控制项  
  
 这些属性将显示在**“属性”**窗口中。  
  
## 功能属性  
 使用**“功能属性”**属性来指定功能所使用的数据。  功能属性数据是在将功能部署到 SharePoint 时功能附带的一组值（以键\/值对的形式存储）。  部署功能之后，您可以在代码中访问属性值。  
  
 将功能属性值添加到项目项时，会将该值以元素的形式添加在项功能的清单中。  举例来说，在业务数据连接 \(BDC\) 模型项目中，ModelFileName 功能属性显示为：  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 设置功能属性值后，会将其作为 FeatureProperty 元素添加在项目的 .spdata 文件中。  有关在 SharePoint 中访问属性的信息，请参见 [SPFeaturePropertyCollection 类 \(Microsoft.SharePoint\)](http://go.microsoft.com/fwlink/?LinkId=177391)。  
  
 在功能清单中，会将来自所有项目项的相同功能属性值合并在一起。  但是，如果两个不同的项目项使用不匹配的值指定相同功能属性键，则会发生验证错误。  
  
 若要将功能属性直接添加到功能文件 \(\*.feature\)，请调用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 对象模型方法 <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>。  如果使用此方法，请注意，有关在“功能属性”中添加相同功能属性值的同一规则也适用于直接添加到功能文件的属性。  
  
## 功能接收器  
 功能接收器是在项目项的包含功能发生某些事件时执行的代码。  例如，您可以定义在安装、激活或升级功能时执行的功能接收器。  添加功能接收器的一种方法是按[演练：添加功能事件接收器](../sharepoint/walkthrough-add-feature-event-receivers.md)中所述的方式将其直接添加到功能。  另一种方法是在**“功能接收器”**属性中引用功能接收器类名和程序集。  
  
### 直接方法  
 将功能接收器直接添加到功能时，会在解决方案资源管理器的**“功能”**节点下放置一个代码文件。  在生成 SharePoint 解决方案时，该代码将编译为程序集并部署到 SharePoint。  默认情况下，功能属性**“接收器程序集”**和**“接收器类”**引用类名和程序集。  
  
### 引用方法  
 添加功能接收器的另一种方法是使用项目项的**“功能接收器”**属性来引用功能接收器程序集。  “功能接收器”属性值具有两个子属性：**“程序集”**和**“类名”**。  程序集必须使用其完全限定“强”名称，并且类名必须为完整的类型名称。  有关更多信息，请参见[具有强名称的程序集](http://go.microsoft.com/fwlink/?LinkID=169573)。  将解决方案部署到 SharePoint 后，功能将使用引用的功能接收器来处理功能事件。  
  
 在解决方案生成时，功能及其项目中的功能接收器属性值将合并在一起，以设置 SharePoint 解决方案 \(.wsp\) 文件的功能清单中 Feature 元素的 ReceiverAssembly 和 ReceiverClass 特性。  因此，如果项目项和功能的“程序集”和“类名”属性值均已指定，则项目项和功能属性值必须匹配。  如果这些值不匹配，您将收到验证错误。  如果希望项目项引用的功能接收器程序集不是其功能使用的功能接收器程序集，请将其移到另一个功能。  
  
 如果引用服务器上尚不存在的功能接收器程序集，您还必须在包中包括程序集文件本身；[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不会为您添加该文件。  在部署功能时，会将程序集文件复制到系统的[!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] 或 SharePoint 物理目录中的 Bin 文件夹。  有关更多信息，请参见操作方法：[如何：添加和移除附加程序集](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 有关功能接收器的更多信息，请参见 [按功能事件接收器](http://go.microsoft.com/fwlink/?LinkID=169574) 和 [提供事件功能](http://go.microsoft.com/fwlink/?LinkID=169575)。  
  
## 项目输出引用  
 “项目输出引用”属性指定项目项需要运行的依赖项（例如程序集）。  例如，假设您的解决方案具有一个 BDC 项目和一个类项目。  如果 BDC 项目依赖于类项目输出的程序集，则可以在 BDC 项目的“项目输出引用”属性中引用该程序集。  在打包 BDC 项目时，依赖程序集将包括在包中。  
  
 项目输出引用通常为程序集，但在某些情况下（例如 Silverlight 项目）也可以为其他文件类型。  
  
 有关详细信息，请参阅[如何：添加项目输出引用](../sharepoint/how-to-add-a-project-output-reference.md)。  
  
## 安全控制项  
 SharePoint 提供了一种称为安全控制项的安全机制，用于限制不受信任的用户对某些控件的访问。  根据设计，SharePoint 允许不受信任的用户在 SharePoint 服务器上上载和创建 ASPX 页。  为了防止这些用户向 ASPX 页中添加不安全的代码，SharePoint 将限制这些用户对安全控件的访问。  安全控件是指定为安全并且可由网站上的任何用户使用的 ASPX 控件和 Web 部件。  有关更多信息，请参见 [步骤 4:将 Web 部件添加到安全的控件列表](http://go.microsoft.com/fwlink/?LinkID=171014)。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的每个 SharePoint 项目项都有一个**安全控件项** 的属性，其包含两个布尔属性**安全** 和 **安全应对脚本**。  安全属性指定不受信任的用户是否能访问控件。  “安全应对脚本”属性指定不受信任的用户是否能查看和更改控件的属性。  
  
 安全控制项是按程序集引用的。  您通过在项目项的**“安全控制项”**属性中输入安全控制项来将这些安全控制项添加到项目的程序集。  不过，您也可以在向包中添加其他程序集时通过**“包设计器”**中的**“高级”**选项卡将安全控制项添加到项目的程序集。  有关更多信息，请参见 [如何：将控件标记为安全控件](../sharepoint/how-to-mark-controls-as-safe-controls.md) 或 [注册一个 Web 部件程序集作为一个安全控件](http://go.microsoft.com/fwlink/?LinkID=171013)。  
  
### 安全控件的 XML 项  
 将安全控制项添加到项目项或项目的程序集时，将采用以下格式向包清单中写入一个引用：  
  
```  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  