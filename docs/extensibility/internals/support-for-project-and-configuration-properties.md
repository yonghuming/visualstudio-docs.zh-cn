---
title: "对项目和配置属性的支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目属性，请使用 Visual Studio SDK 支持"
  - "配置属性，与 Visual Studio SDK suppporting"
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 对项目和配置属性的支持
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**属性** 中的窗口 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成的开发环境 \(IDE\) 可以显示的项目和配置属性。 以便用户可以设置您的应用程序的属性，您可以提供您自己的项目类型的属性页。  
  
 通过选择项目节点中的 **解决方案资源管理器** ，然后单击 **属性** 上 **项目** 菜单上，可以打开一个对话框，其中包括项目和配置属性。 在 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], ，和项目类型派生自这些语言，此对话框中显示为选项卡式页面 [“选项”对话框 \-\>“环境”\-\>“常规”](../../ide/reference/general-environment-options-dialog-box.md)。 有关详细信息，请参阅 [不在生成︰ 演练︰ 公开项目和配置属性 \(C\#\)](http://msdn.microsoft.com/zh-cn/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)。  
  
 对于项目 \(MPFProj\) 管理软件包框架提供了用于创建和管理新的项目系统的帮助器类。 您可以找到源处的代码和编译说明 [项目\-Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
## 项目和配置属性的持久性  
 项目和配置的属性保存在一个具有文件扩展名与项目类型，例如关联、.csproj、.vbproj 和.myproj 的项目文件中。 语言项目通常使用的模板文件生成的项目文件。 但是，有很实际多种项目类型和模板进行关联。 有关详细信息，请参阅 [NIB: Visual Studio 模板](http://msdn.microsoft.com/zh-cn/141fccaa-d68f-4155-822b-27f35dd94041) 和 [模板目录说明 \(。Vsdir\) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
 通过将项添加到模板文件创建项目和配置属性。 然后，这些属性是可供使用的项目类型的使用此模板创建的任何项目。[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项目和两种方法使用的 MPFProj [不在生成︰ MSBuild 概述](http://msdn.microsoft.com/zh-cn/b588fd73-a45b-4706-908f-cc131bccfbde) 模板文件的架构。 这些文件具有每个配置的 PropertyGroup 部分。 项目的属性通常保留在具有配置参数设置为空字符串的第一个 PropertyGroup 部分中。  
  
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
  
 在此项目文件中， `<Name>` 和 `<SchemaVersion>` 是项目属性和 `<Optimize>` 是配置属性。  
  
 它负责要保存项目文件的项目和配置属性的项目。  
  
> [!NOTE]
>  一个项目可以通过保留唯一属性值不同于其默认值来优化持久性。  
  
## 对项目和配置属性的支持  
 `Microsoft.VisualStudio.Package.SettingsPage` 类实现项目和配置的属性页。 默认实现 `SettingsPage` 到泛型属性网格中的用户提供的公共属性。`Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` 方法选择从派生的类 `SettingsPage` 项目属性网格。`Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` 方法选择从派生的类 `SettingsPage` 配置属性网格。 您的项目类型应重写这些方法来选择相应的属性页。  
  
 `SettingsPage` 类和 `Microsoft.VisualStudio.Package.ProjectNode` 类提供这些方法以持久保存项目和配置属性︰  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 和 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` 持久保存项目属性。  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 和 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 持久保存配置属性。  
  
    > [!NOTE]
    >  实现 `Microsoft.VisualStudio.Package.SettingsPage` 和 `Microsoft.VisualStudio.Package.ProjectNode` 类使用 `Microsoft.Build.BuildEngine` \(MSBuild\) 方法来获取和设置从项目文件的项目和配置属性。  
  
 从中派生的类 `SettingsPage` 必须实现 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` 和 `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` 来持久保存的项目文件的项目或配置属性。  
  
## ProvideObjectAttribute 和注册表路径  
 类派生自 `SettingsPage` 设计为在 VSPackages 迁移之间共享。 若要使 VSPackage 创建派生自的类 `SettingsPage`, ，添加 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 从派生类 `Microsoft.VisualStudio.Shell.Package`。  
  
 [!code-cs[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 该属性附加到 VSPackage 并不重要。 当注册 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，注册的任何对象的可创建的类 id \(CLSID\)，以便调用 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 可以创建它。  
  
 可以创建的对象的注册表路径由组合 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, ，word、 CLSID、 和的对象类型的 guid。 如果 `MyProjectPropertyPage` 类具有一个 guid {3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} 并且 UserRegistryRoot HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp，则注册表路径将为 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\CLSID\\{3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723}。  
  
## 项目和配置属性的特性和布局  
 <xref:System.ComponentModel.CategoryAttribute>, ，<xref:System.ComponentModel.DisplayNameAttribute>, ，和 <xref:System.ComponentModel.DescriptionAttribute> 特性确定布局、 标签和通用的属性页中的项目和配置属性的说明。 这些属性确定的类别，分别显示名称和描述的选项。  
  
> [!NOTE]
>  等效属性、 SRCategory、 LocDisplayName 和 SRDescription，使用用于本地化的字符串资源和中定义 [项目\-Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 考虑以下代码片断：  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-cs[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp` 配置属性显示在配置属性页作为 **我的配置属性** 在类别中， **My Category**。 如果选项，该说明， **我说明**, ，会出现在描述面板。  
  
## 请参阅  
 [不在生成︰ 演练︰ 公开项目和配置属性 \(C\#\)](http://msdn.microsoft.com/zh-cn/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [添加和删除属性页](../../extensibility/adding-and-removing-property-pages.md)   
 [VSPackage 状态](/visual-cpp/misc/vspackage-state)   
 [项目](../../extensibility/internals/projects.md)   
 [NIB：Visual Studio 模板](http://msdn.microsoft.com/zh-cn/141fccaa-d68f-4155-822b-27f35dd94041)   
 [模板目录说明 \(。Vsdir\) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)