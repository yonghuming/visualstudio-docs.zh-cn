---
title: "选项和选项页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具选项页 [Visual Studio SDK]，管理包框架支持"
  - "托管的包框架、 工具选项页的支持"
  - "工具选项页的支持"
  - "工具选项页 [Visual Studio SDK]，布局"
  - "工具选项页 [Visual Studio SDK] 属性"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# 选项和选项页
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

单击 **选项** 上 **工具** 菜单打开 **选项** 对话框。 在此对话框中选项统称为选项页。 在导航窗格中的树控件包括选项类别和每个类别都具有选项页。 当您选择一个页面时，其选项出现在右窗格中。 这些页面，您可以更改确定作为 VSPackage 的状态的选项的值。  
  
## 支持选项页  
 <xref:Microsoft.VisualStudio.Shell.Package> 类用于创建选项页和选项类别提供支持。<xref:Microsoft.VisualStudio.Shell.DialogPage> 类实现选项页。  
  
 默认实现 <xref:Microsoft.VisualStudio.Shell.DialogPage> 到一个通用的属性网格中的用户提供其公共属性。 通过重写要创建具有其自己的用户界面 \(UI\) 的自定义选项页的页面上的各种方法，可以自定义此行为。 有关详细信息，请参阅[创建选项页](../../extensibility/creating-an-options-page.md)。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> 类实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager>, ，为用户设置选项页，还提供持久性。 默认实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 和 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法持久保存到注册表的用户部分的属性更改，如果该属性可以和从字符串进行转换。  
  
## 选项页上的注册表路径  
 默认情况下，由选项页的属性的注册表路径由组合 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, ，word DialogPage 和选项页类的类型名称。 例如，可能会如下所示定义选项页类。  
  
 [!CODE [VSSDKSupportForOptionsPages#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#1)]  
  
 如果 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> 为 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp，则属性名称 \/ 值对的 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral 子项。  
  
 选项页本身的注册表路径由组合 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, ，单词、 ToolsOptionsPages，和选项页上类别和名称。 例如，如果了类别，我的选项页面，自定义选项页和 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> 为 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp，则选项页上都具有该注册表项，HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My 选项 Pages\\Custom。  
  
## 工具\/选项页属性和布局  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 属性确定分组的自定义选项页的导航树中的类别为 **选项** 对话框。<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 属性将选项页与提供的接口 VSPackage 相关联。 考虑以下代码片断：  
  
 [!CODE [VSSDKSupportForOptionsPages#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#2)]  
  
 此声明 MyPackage 提供了两个选项页，OptionsPageGeneral 和 OptionsPageCustom。 在 **选项** 对话框中，这两个选项页将出现在 **我选项页** 与类别 **常规** 和 **自定义**, 分别。  
  
## 选项属性和布局  
 页上提供的用户界面 \(UI\) 确定自定义选项页中选项的外观。 以下属性确定布局、 标签和通用选项页中的选项的说明︰  
  
-   <xref:System.ComponentModel.CategoryAttribute> 确定选项的类别。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> 确定选项的显示名称。  
  
-   <xref:System.ComponentModel.DescriptionAttribute> 确定对选项的说明。  
  
    > [!NOTE]
    >  等效属性、 SRCategory、 LocDisplayName 和 SRDescription，使用用于本地化的字符串资源和中定义 [托管的项目示例](http://go.microsoft.com/fwlink/?LinkId=122774)。  
  
 考虑以下代码片断：  
  
 [!CODE [VSSDKSupportForOptionsPages#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#3)]  
  
 作为选项页将显示该 OptionInteger 选项 **整数选项** 中 **我选项** 类别。 如果选项，说明， **我整数选项**, ，将显示在说明框中。  
  
## 从另一个 VSPackage 访问选项页  
 承载和管理选项页的 VSPackage 可以以编程方式访问从另一个 VSPackage 使用自动化模型。 例如，下面的代码中 VSPackage 注册为承载某一选项页。  
  
 [!CODE [VSSDKSupportForOptionsPages#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#4)]  
  
 下面的代码片段获取从 MyOptionPage OptionInteger 的值︰  
  
 [!CODE [VSSDKSupportForOptionsPages#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#5)]  
  
 当 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 属性注册选项页，页上注册下 AutomationProperties 密钥 if `SupportsAutomation` 参数的属性是 `true`。 自动化检查此注册表项以查找相关联的 VSPackage 和自动化，然后通过托管的选项页中，在这种情况下，我的网格页中访问的属性。  
  
 通过组合确定的自动化属性的注册表路径 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, ，单词、 AutomationProperties，和选项页上类别和名称。 例如，如果选项页具有 My Category 类别中，我的网格页名称和 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, ，HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp，则该自动化属性有注册表项，HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My Category\\My 网格页。  
  
> [!NOTE]
>  规范名称，我 Category.My 网格页中，是此项的名称子项的值。