---
title: "创建选项页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 56a51aa0a2232ff149e1959842fced1dc26e7c1b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-options-pages"></a>创建选项页
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]托管的包框架类派生自<xref:Microsoft.VisualStudio.Shell.DialogPage>扩展[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE，方法是添加**选项**下页**工具**菜单。</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 一个对象，实现给定**工具选项**页是与特定 VSPackages 迁移通过关联<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>对象。</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 因为环境都实例化实现特定的对象**工具选项**页时 IDE 将显示该特定页︰  
  
-   一个**工具选项**应实现页上，在其自己的对象，而不是在实现 VSPackage 的对象。  
  
-   对象不能实现多个**工具选项**页。  
  
## <a name="registering-as-a-tools-options-page-provider"></a>注册为工具选项页提供程序  
 VSPackage 支持用户配置通过**工具选项**页指示的对象提供这些**工具选项**通过应用的实例的页<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>应用于<xref:Microsoft.VisualStudio.Shell.Package>实现。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 必须有的一个实例<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>为每个<xref:Microsoft.VisualStudio.Shell.DialogPage>的派生类型实现**工具选项**页。</xref:Microsoft.VisualStudio.Shell.DialogPage> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 每个实例<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>使用实现类型**工具选项**页上，字符串，其中包含的类别和子类别用来标识**工具选项**页上，并将该类型注册为提供的资源信息**工具选项**页。</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
## <a name="persisting-tools-options-page-state"></a>保留工具选项页状态  
 如果**工具选项**页的实现注册自动化启用了支持，IDE 保持页面的状态以及所有其他**工具选项**页。  
  
 通过使用<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> VSPackage 可以管理其自己的持久性 应使用只有一个或另一个方法的持久性。  
  
## <a name="implementing-dialogpage-class"></a>实现 DialogPage 类  
 对象，用于提供的 VSPackage 实现<xref:Microsoft.VisualStudio.Shell.DialogPage>的派生的类型可以利用以下继承功能︰</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
-   默认用户界面窗口。  
  
-   一个默认持久性机制可用任一 if<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>应用于类，或者如果<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>属性设置为`true`有关<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>应用于该类</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute></xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A></xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
-   自动化支持。  
  
 一个对象，实现的最低要求**工具选项**页上使用<xref:Microsoft.VisualStudio.Shell.DialogPage>是公共属性的补充。</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 如果该类正确地注册为**工具选项**页提供程序，然后对其公共属性都位于**选项**部分**工具**属性网格的窗体菜单中。  
  
 可以重写所有这些默认的功能。 例如，若要创建更复杂用户界面需要仅重写的默认实现的<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>。</xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>  
  
## <a name="example"></a>示例  
 后面是选项页的"你好世界"的简单实现。 将以下代码添加到默认的项目中创建的 Visual Studio 包模板与**菜单命令**选项处于选中状态充分地演示选项页的功能。  
  
### <a name="description"></a>说明  
 下面的类定义的最小"你好世界"选项页。 打开时，用户可以设置公共`HelloWorld`在属性网格中的属性。  
  
### <a name="code"></a>代码  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>描述  
 将以下特性应用于程序包类使页上的选项可加载包时。 数字是任意资源 Id 为类别和页，并在结束的布尔值指定页上是否支持自动化。  
  
### <a name="code"></a>代码  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>说明  
 以下事件处理程序显示在选项页中设置的属性根据值结果。 它使用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>方法的结果显式转换为自定义选项页类型，以访问页上公开的属性。</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>  
  
 对于由包模板生成项目，调用该函数从`MenuItemCallback`函数以将其附加到默认命令添加到**工具**菜单。  
  
### <a name="code"></a>代码  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [扩展的用户设置和选项](../../extensibility/extending-user-settings-and-options.md)   
 [选项页的自动化支持](../../extensibility/internals/automation-support-for-options-pages.md)
