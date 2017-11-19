---
title: "选项和选项页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 665567430ac9fdfdc301329972a3a4f7b621a241
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="options-and-options-pages"></a>选项和选项页
单击**选项**上**工具**打开菜单**选项**对话框。 在此对话框中的选项统称为选项页。 在导航窗格中的树控件包含选项类别，每个类别包含选项页。 当选择页时，其选项出现在右窗格中。 这些页面允许您更改确定 VSPackage 的状态选项的值。  
  
## <a name="support-for-options-pages"></a>支持选项页  
 <xref:Microsoft.VisualStudio.Shell.Package>类用于创建选项页和选项类别提供支持。 <xref:Microsoft.VisualStudio.Shell.DialogPage>类实现的选项页。  
  
 默认实现<xref:Microsoft.VisualStudio.Shell.DialogPage>到一个通用的属性网格中的用户提供对其公共属性。 你可以通过重写页后，可以创建具有其自己的用户界面 (UI) 的自定义选项页上的各种方法来自定义此行为。 有关详细信息，请参阅[创建选项页](../../extensibility/creating-an-options-page.md)。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>类实现<xref:Microsoft.VisualStudio.Shell.IProfileManager>，该属性提供持久性选项页，还负责用户设置。 默认实现<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>和<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>方法持久保存到注册表的用户部分的属性更改，如果可以转换属性，或从字符串。  
  
## <a name="options-page-registry-path"></a>选项页注册表路径  
 默认情况下，由选项页的属性的注册表路径确定通过组合<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>，word DialogPage 和选项页类的类型名称。 例如，可能会如下所示定义选项页类。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 如果<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>为 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，则属性名称和值对的 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ 子项Company.OptionsPage.OptionsPageGeneral。  
  
 选项页本身的注册表路径确定通过组合<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，单词、 ToolsOptionsPages，和选项页上执行的类别和名称。 例如，如果自定义选项页具有类别、 我的选项页和<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>为 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，则选项页都具有注册表项，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My 选项 Pages\Custom。  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>工具/选项页属性和布局  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性确定在的导航树中的类别的自定义选项页分组**选项**对话框。 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性将与提供的接口的 VSPackage 相关联的选项页。 考虑以下代码片断：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 这会将声明 MyPackage 提供两个选项页，OptionsPageGeneral 和 OptionsPageCustom。 在**选项**中显示的对话框中，这两个选项页**我的选项页面**作为类别**常规**和**自定义**分别。  
  
## <a name="option-attributes-and-layout"></a>选项特性和布局  
 此页提供了用户界面 (UI) 确定自定义选项页中选项的外观。 布局、 标签和通用选项页中的选项的说明确定以下属性：  
  
-   <xref:System.ComponentModel.CategoryAttribute>确定选项的类别。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>确定选项的显示名称。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>确定选项的说明。  
  
    > [!NOTE]
    >  等效属性、 SRCategory、 LocDisplayName 和 SRDescription，用于本地化的字符串资源，并在中定义[托管的项目示例](http://go.microsoft.com/fwlink/?LinkId=122774)。  
  
 考虑以下代码片断：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 在为选项页上会显示该 OptionInteger 选项**整数选项**中**我选项**类别。 如果选择了选项，说明，**我整数选项**，将显示在描述框中。  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>从另一个 VSPackage 访问选项页  
 承载和管理选项页的 VSPackage 可以以编程方式访问从另一个 VSPackage 使用自动化模型。 例如，下面的代码在 VSPackage 注册为承载选项页。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 下面的代码段从 MyOptionPage 获取的 OptionInteger 的值：  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 当<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性中注册的选项页、 在 AutomationProperties 密钥如果下注册页`SupportsAutomation`属性的自变量是`true`。 自动化检查此注册表项，找到关联的 VSPackage 和自动化，然后通过托管的选项页上，在这种情况下，我的网格网页访问该属性。  
  
 注册表路径的自动化属性确定通过组合<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，单词、 AutomationProperties，和选项页上执行的类别和名称。 例如，如果选项页具有我类别类别，我网格页名称，与<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp，然后的自动化属性必须注册表项，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My 网格页。  
  
> [!NOTE]
>  规范名称，我 Category.My 网格页上，是此项的名称子项的值。