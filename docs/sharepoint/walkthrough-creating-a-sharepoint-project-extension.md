---
title: "演练： 创建 SharePoint 项目扩展 |Microsoft 文档"
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
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1974f32731d8ba45b2210b9d9231a7e69d6905f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-sharepoint-project-extension"></a>演练：创建 SharePoint 项目扩展
  本演练阐释了如何创建 SharePoint 项目扩展。 项目扩展可用于响应项目级事件，如当添加、 删除或重命名项目。 你可以添加自定义属性，或当属性值更改时进行响应。 与项目项扩展不同项目扩展不能与特定的 SharePoint 项目类型关联。 当你创建项目扩展时，该扩展加载任何类型的 SharePoint 项目中打开时[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
 在本演练中，你将创建自定义的布尔值属性添加到任何 SharePoint 项目中创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 当设置为**True**，新属性添加，或映射到你的项目的图像资源文件夹。 当设置为**False**，删除 Images 文件夹中，如果它存在。 有关详细信息，请参阅[如何： 添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 本演练演示了下列任务：  
  
-   创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]为 SharePoint 项目扩展，执行下列任务：  
  
    -   将自定义项目属性添加到属性窗口。 属性适用于任何 SharePoint 项目。  
  
    -   使用 SharePoint 项目对象模型向项目中添加的映射的文件夹。  
  
    -   使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]自动化对象模型 (DTE) 从项目中删除映射的文件夹。  
  
-   生成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包来部署项目属性的扩展程序集。  
  
-   调试和测试项目属性。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练的开发计算机上：  
  
-   支持的版本的[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]，SharePoint 和[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本演练使用**VSIX 项目**中的模板[!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)]创建 VSIX 包来部署项目的属性扩展。 有关详细信息，请参阅[扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="creating-the-projects"></a>创建项目  
 若要完成本演练，必须创建两个项目：  
  
-   若要创建 VSIX 包来部署项目扩展一个 VSIX 项目。  
  
-   一个用于实现项目扩展的库项目。  
  
 首先演练创建项目。  
  
#### <a name="to-create-the-vsix-project"></a>若要创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
3.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**扩展性**节点。  
  
    > [!NOTE]  
    >  此节点是安装 Visual Studio SDK 时才可用。 有关详细信息，请参阅本主题前面的先决条件部分。  
  
4.  在对话框中的顶部，选择**.NET Framework 4.5**的版本的.NET Framework 中，列表中，然后选择**VSIX 项目**模板。  
  
5.  在**名称**框中，输入**ProjectExtensionPackage**，然后选择**确定**按钮。  
  
     **ProjectExtensionPackage**项目将出现在**解决方案资源管理器**。  
  
#### <a name="to-create-the-extension-project"></a>若要创建扩展项目  
  
1.  在**解决方案资源管理器**，打开解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
2.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**Windows**。  
  
3.  在对话框中的顶部，选择**.NET Framework 4.5**的版本的.NET Framework 中，列表中，然后选择**类库**项目模板。  
  
4.  在**名称**框中，输入**ProjectExtension**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**ProjectExtension**到解决方案的项目并打开默认 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## <a name="configuring-the-project"></a>配置项目  
 在编写代码以创建项目扩展之前，添加代码文件和向扩展项目的程序集引用。  
  
#### <a name="to-configure-the-project"></a>若要配置项目  
  
1.  添加名为的代码文件**为 CustomProperty**到 ProjectExtension 项目。  
  
2.  打开的快捷菜单**ProjectExtension**项目，，然后选择**添加引用**。  
  
3.  在**引用管理器-为 CustomProperty**对话框框中，选择**Framework**节点，，然后选择的 System.ComponentModel.Composition 和 System.Windows.Forms 程序集旁边的复选框。  
  
4.  选择**扩展**节点，选择 Microsoft.VisualStudio.SharePoint 和 EnvDTE 程序集，旁边的复选框，然后选择**确定**按钮。  
  
5.  在**解决方案资源管理器**下**引用**文件夹**ProjectExtension**项目，选择**EnvDTE**。  
  
6.  在**属性**窗口中，更改**嵌入互操作类型**属性**False**。  
  
## <a name="defining-the-new-sharepoint-project-property"></a>定义新的 SharePoint 项目属性  
 创建定义项目扩展和新的项目属性的行为的类。 若要定义新项目扩展，此类应实现<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>接口。 无论何时你想要定义 SharePoint 项目扩展，则实现此接口。 此外，将添加<xref:System.ComponentModel.Composition.ExportAttribute>到类。 使用此属性，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]能够发现和加载你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>实现。 传递<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>类型设置为该特性的构造函数。  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>若要定义新的 SharePoint 项目属性  
  
1.  将以下代码粘贴到为 CustomProperty 代码文件。  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="building-the-solution"></a>生成解决方案  
 接下来，生成解决方案以确保它在编译时没有错误。  
  
#### <a name="to-build-the-solution"></a>生成解决方案  
  
1.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-property-extension"></a>创建 VSIX 包来部署项目的属性扩展  
 若要部署项目扩展，使用 VSIX 项目解决方案中创建 VSIX 包。 首先，通过修改 VSIX 项目中包含的 source.extension.vsixmanifest 文件中配置 VSIX 包。 然后，通过生成解决方案中创建 VSIX 包。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要配置并创建 VSIX 包  
  
1.  在**解决方案资源管理器**，打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**打开**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]在清单设计器中打开文件。 在显示的信息**元数据**选项卡也将出现在**扩展和更新**。 所有 VSIX 包都需要 extension.vsixmanifest 文件。 有关此文件的详细信息，请参阅[VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**产品名称**框中，输入**自定义项目属性**。  
  
3.  在**作者**框中，输入**Contoso**。  
  
4.  在**说明**框中，输入**自定义 SharePoint 项目属性，用于切换到项目的图像资源文件夹的映射**。  
  
5.  选择**资产**选项卡上，然后选择**新建**按钮。  
  
     **添加新资产**对话框随即出现。  
  
6.  在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于`MEFComponent`extension.vsixmanifest 文件中的元素。 此元素指定的 VSIX 包中的扩展程序集的名称。 有关详细信息，请参阅[MEFComponent 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**源**列表中，选择**当前解决方案中的项目**选项按钮。  
  
8.  在**项目**列表中，选择**ProjectExtension**。  
  
     此值标识你正在项目中生成的程序集的名称。  
  
9. 选择**确定**关闭**添加新资产**对话框。  
  
10. 在菜单栏上，选择**文件**，**保存所有**当您完成，，然后关闭清单设计器。  
  
11. 在菜单栏上，选择**生成**，**生成解决方案**，并确保该项目在编译时没有错误。  
  
12. 在**解决方案资源管理器**，打开快捷菜单**ProjectExtensionPackage**项目，然后选择**在文件资源管理器中打开文件夹**按钮。  
  
13. 在**文件资源管理器**打开 ProjectExtensionPackage 项目的生成输出文件夹，然后验证该文件夹包含名为 ProjectExtensionPackage.vsix 的文件。  
  
     默认情况下，生成输出文件夹是...在包含你的项目文件的文件夹下的 \bin\Debug 文件夹。  
  
## <a name="testing-the-project-property"></a>测试项目属性  
 你现在可以测试自定义项目属性。 调试和测试新的项目属性扩展的实验实例中最容易[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 此实例[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]运行 VSIX 或其他扩展性项目时创建。 调试项目后，你可以在你的系统上安装扩展，然后继续进行调试和测试中的正则实例[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>调试和测试的 Visual Studio 的实验实例中的扩展  
  
1.  重新启动[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]与管理凭据，然后打开 ProjectExtensionPackage 解决方案。  
  
2.  启动你的项目的调试版本，请选择**F5**关键的或在菜单栏中，选择**调试**，**启动调试**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]到 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 项目 Property\1.0 安装扩展和启动的实验实例[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
3.  在实验实例中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、 创建场解决方案，一个 SharePoint 项目和在向导中的其他值中使用的默认值。  
  
    1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
    2.  在顶部**新项目**对话框框中，选择**.NET Framework 3.5**在列表中的.NET framework 的版本。  
  
         SharePoint 工具扩展需要在此版本的功能[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]。  
  
    3.  下**模板**节点，展开**Visual C#**或**Visual Basic**节点，选择**SharePoint**节点，然后选择**2010年**节点。  
  
    4.  选择**SharePoint 2010 项目**模板，然后输入**ModuleTest**作为你的项目的名称。  
  
4.  在**解决方案资源管理器**，选择**ModuleTest**项目节点。  
  
     新的自定义属性**地图图像文件夹**出现在**属性**窗口默认值为**False**。  
  
5.  更改到该属性的值**True**。  
  
     映像资源文件夹添加到 SharePoint 项目。  
  
6.  将更改该属性的值回**False**。  
  
     如果你选择**是**按钮**删除映像文件夹？**对话框中，从 SharePoint 项目中删除资源文件夹的映像。  
  
7.  关闭 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的实验实例。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 项目](../sharepoint/extending-sharepoint-projects.md)   
 [如何： 向 SharePoint 项目中添加属性](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [SharePoint 项目系统类型和其他 Visual Studio 项目类型之间进行转换](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [扩展 SharePoint 项目系统中保存数据](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [将自定义数据与 SharePoint 工具扩展相关联](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  