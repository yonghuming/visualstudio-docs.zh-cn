---
title: "提供打包和部署信息在项目项中的 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5f12b3af8f49270cc914e47a37077265794bf0be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Providing Packaging and Deployment Information in Project Items
  中的所有 SharePoint 项目项[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有可用于项目部署到 SharePoint 时提供额外的数据的属性。 这些属性如下所示：  
  
-   功能属性  
  
-   功能接收器  
  
-   项目输出引用  
  
-   安全控件项  
  
 这些属性将显示在**属性**窗口。  
  
## <a name="feature-properties"></a>功能属性  
 使用**功能属性**属性以指定的功能使用的数据。 功能属性数据是一组值 （以键/值对的形式存储），部署到 SharePoint 时所随附一项功能。 部署功能后，可在代码中访问属性值。  
  
 当项目项中添加功能属性值时，值被添加的项的功能的清单中的元素。 在业务数据连接 (BDC) 模型项目中，例如，ModelFileName 功能属性显示为：  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 设置功能属性值后，则将它添加为项目的.spdata 文件中的 FeatureProperty 元素。 有关访问 SharePoint 中的属性的信息，请参阅[SPFeaturePropertyCollection 类](http://go.microsoft.com/fwlink/?LinkId=177391)。  
  
 功能清单中，从项目的所有项目的相同的功能属性值合并到一起。 但是，如果两个不同的项目项不匹配的值与指定相同的功能属性键，则发生验证错误。  
  
 若要将功能属性添加直接到功能文件 (*.feature)，调用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 对象模型方法<xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>。 如果你使用此方法，请注意有关添加相同的功能属性值的功能属性相同的规则也适用于将直接添加到功能文件的属性。  
  
## <a name="feature-receiver"></a>功能接收器  
 功能接收器是包含的功能在项目项发生特定事件时执行的代码。 例如，你可以定义在安装、 激活，或升级功能时执行的功能接收器。 添加功能接收器是将其添加到功能直接中所述的一种方法[演练： 添加功能事件接收器](../sharepoint/walkthrough-add-feature-event-receivers.md)。 另一种方法是一个功能接收器类名和中的程序集引用**功能接收器**属性。  
  
### <a name="direct-method"></a>直接方法  
 当直接添加到功能的功能接收器时，代码文件被放在**功能**在解决方案资源管理器中的节点。 在创建 SharePoint 解决方案时，该代码将编译到程序集，并部署到 SharePoint。 默认情况下，功能属性**接收器程序集**和**接收器类**引用类名称和程序集。  
  
### <a name="reference-method"></a>Reference 方法  
 功能接收器中添加另一种方法是使用**功能接收器**用于引用功能接收器程序集的项目项的属性。 功能接收器属性值具有两个子属性：**程序集**和**类名**。 程序集必须使用其完全限定，"强"名称和类名必须是完整类型名称。 有关详细信息，请参阅[具有强名称的程序集](http://go.microsoft.com/fwlink/?LinkID=169573)。 将解决方案部署到 SharePoint 之后, 该功能用引用的功能接收器来处理功能的事件。  
  
 在解决方案生成期间，在功能和其项目中的功能接收器属性值合并在一起的 SharePoint 解决方案 (.wsp) 文件的功能清单中设置的功能元素的 ReceiverAssembly 和 ReceiverClass 属性。 因此，如果项目项和功能的程序集和类名称属性值都已指定，则项目项和功能属性值必须匹配。 如果值不匹配，你将收到验证错误。 如果你希望项目项引用的功能接收器程序集不是其功能使用，将其移到另一项功能。  
  
 如果引用已不在服务器的功能接收器程序集，还必须在包中包含程序集文件本身[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不会为你添加它。 在部署功能时，将程序集文件复制到系统的[!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)]或 SharePoint 物理目录中的 Bin 文件夹。 有关详细信息，请参阅如何：[如何： 添加和移除附加程序集](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 有关功能接收器的详细信息，请参阅[功能事件接收器](http://go.microsoft.com/fwlink/?LinkID=169574)和[功能事件](http://go.microsoft.com/fwlink/?LinkID=169575)。  
  
## <a name="project-output-references"></a>项目输出引用  
 项目输出引用属性指定的依赖项，如您的项目项运行所需的程序集。 例如，假设你的解决方案有 BDC 项目和类项目。 如果 BDC 项目的输出： 类项目的程序集具有的依赖关系，则可以引用 BDC 项目的项目输出引用属性中的程序集。 打包 BDC 项目时，依赖程序集包括在包中。  
  
 项目输出引用通常是程序集，但在某些情况下 （例如 Silverlight 项目） 可以是其他文件类型。  
  
 有关详细信息，请参阅[如何： 添加项目输出引用](../sharepoint/how-to-add-a-project-output-reference.md)。  
  
## <a name="safe-control-entries"></a>安全控件项  
 SharePoint 提供名为安全控件项，以限制到特定控件的不受信任用户的访问的安全机制。 按照设计，SharePoint 允许不受信任的用户能够上载和 SharePoint 服务器上创建 ASPX 页。 为了防止这些用户将不安全的代码添加到 ASPX 页，SharePoint 会限制其访问权限*安全控件*。 安全控件 ASPX 控件和 Web 部件指定为安全并且可由你的站点上的任何用户。 有关详细信息，请参阅[步骤 4： 将 Web 部件添加到安全的控件列表](http://go.microsoft.com/fwlink/?LinkID=171014)。  
  
 中的每个 SharePoint 项目项[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有称为属性**安全控件项**具有两个布尔子属性：**安全**和**安全应对脚本**。 “安全”属性指定不受信任的用户是否能访问控件。 安全应对脚本属性指定不受信任的用户是否可以查看和更改控件的属性。  
  
 安全控件项集进行引用。 通过在输入中的项目项的安全控制项添加到项目的程序集**安全控件项**属性。 但是，你还可以向项目的程序集通过添加安全控件项**高级**选项卡中**包设计器**时向包中添加其他程序集。 有关详细信息，请参阅[如何： 为安全控件的标记控件](../sharepoint/how-to-mark-controls-as-safe-controls.md)或[将 Web 部件程序集注册为安全控件](http://go.microsoft.com/fwlink/?LinkID=171013)。  
  
### <a name="xml-entries-for-safe-controls"></a>XML 项的安全控件  
 在添加安全控件项的项目项或属于项目的程序集时，引用写入包清单中的以下格式：  
  
```xml  
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
  
## <a name="see-also"></a>另请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  