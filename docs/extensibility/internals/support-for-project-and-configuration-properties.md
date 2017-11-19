---
title: "支持项目和配置属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1490c350a9c2c5fc91d516e2658c47a8246eb5d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="support-for-project-and-configuration-properties"></a>支持项目和配置属性
**属性**中的窗口[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 可以显示项目和配置属性。 可以为你自己的项目类型提供属性页，以便用户可以设置你的应用程序的属性。  
  
 通过选择中的项目节点**解决方案资源管理器**，然后单击**属性**上**项目**菜单上，你可以打开一个对话框，包括项目和配置属性。 在[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]，和项目类型派生自这些语言的此对话框中显示为选项卡式页面[常规、 环境、 选项对话框](../../ide/reference/general-environment-options-dialog-box.md)。 有关详细信息，请参阅[不在生成： 演练： 公开项目和配置属性 (C#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)。  
  
 托管包框架，用于项目 (MPFProj) 提供用于创建和管理新的项目系统的帮助器类。 你可找到源代码和编译说明[项目的 Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
## <a name="persistence-of-project-and-configuration-properties"></a>项目和配置属性的持久性  
 具有与项目类型，例如关联的文件扩展名、.csproj、.vbproj 和.myproj 项目文件中保留项目和配置属性。 语言项目通常使用的模板文件生成的项目文件。 但是，有实际多种项目类型和模板进行关联。 有关详细信息，请参阅[NIB: Visual Studio 模板](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)和[模板目录说明 (。Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
 通过将项添加到模板文件创建项目和配置属性。 然后，这些属性是可用于通过使用此模板的项目类型创建任何项目。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]项目和两个使用 MPFProj[不在生成： MSBuild 概述](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde)模板文件的架构。 这些文件具有每个配置一个 PropertyGroup 节。 配置参数设置为 null 的字符串的第一 PropertyGroup 节通常保留的项目的属性。  
  
 下面的代码演示了基本的 MSBuild 项目文件的开头。  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 在此项目文件中，`<Name>`和`<SchemaVersion>`是项目属性和`<Optimize>`是配置属性。  
  
 它负责要保存项目文件的项目和配置属性的项目。  
  
> [!NOTE]
>  一个项目可通过保留唯一的属性值不同于其默认值优化持久性。  
  
## <a name="support-for-project-and-configuration-properties"></a>支持项目和配置属性  
 `Microsoft.VisualStudio.Package.SettingsPage`类实现项目和配置属性页。 默认实现`SettingsPage`到泛型属性网格中的用户提供公共属性。 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`方法选择从派生的类`SettingsPage`项目属性网格。 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`方法选择从派生的类`SettingsPage`配置属性网格。 你的项目类型应重写这些方法来选择适当的属性页。  
  
 `SettingsPage`类和`Microsoft.VisualStudio.Package.ProjectNode`类提供这些方法以保持项目和配置属性：  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`和`Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`保留项目属性。  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`和`Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty`保留配置属性。  
  
    > [!NOTE]
    >  实现`Microsoft.VisualStudio.Package.SettingsPage`和`Microsoft.VisualStudio.Package.ProjectNode`类使用`Microsoft.Build.BuildEngine`(MSBuild) 方法来获取和设置从项目文件的项目和配置属性。  
  
 从派生的类`SettingsPage`必须实现`Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges`和`Microsoft.VisualStudio.Package.SettingsPage.BindProperties`以保留的项目文件的项目或配置属性。  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 和注册表路径  
 类派生自`SettingsPage`旨在在 Vspackage 之间共享。 若要使 VSPackage 来创建派生自的类`SettingsPage`，添加`Microsoft.VisualStudio.Shell.ProvideObjectAttribute`类派生自`Microsoft.VisualStudio.Shell.Package`。  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 该属性附加到 VSPackage 并不重要。 使用注册 VSPackage 时[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，注册可以创建任何对象的类 id (CLSID)，以便调用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>可以创建它。  
  
 可以创建的对象的注册表路径确定通过组合<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>，word、 CLSID 和对象类型的 guid。 如果`MyProjectPropertyPage`类具有的 {3c693da2-5bca-49b3-bd95-ffe0a39dd723} guid 和 UserRegistryRoot 为 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，则注册表路径将为 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}。  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>项目和配置属性的特性和布局  
 <xref:System.ComponentModel.CategoryAttribute>， <xref:System.ComponentModel.DisplayNameAttribute>，和<xref:System.ComponentModel.DescriptionAttribute>特性确定布局、 标签和说明的泛型属性页中的项目和配置属性。 这些特性确定的类别，分别显示名称和描述的选项。  
  
> [!NOTE]
>  等效属性、 SRCategory、 LocDisplayName 和 SRDescription，用于本地化的字符串资源，并在中定义[项目的 Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 考虑以下代码片断：  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp`配置属性显示在为此配置属性页**我的配置属性**类别中**我类别**。 如果选择了选项，说明，**我说明**，将显示在说明面板。  
  
## <a name="see-also"></a>另请参阅  
 [添加和删除属性页](../../extensibility/adding-and-removing-property-pages.md)   
 [项目](../../extensibility/internals/projects.md)   
 [模板目录说明 (.Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)