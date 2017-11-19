---
title: "创建选项页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6329950b3af0b0ec44347ad9a85124ee7192439
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-options-pages"></a>创建选项页
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]托管的包框架类派生自<xref:Microsoft.VisualStudio.Shell.DialogPage>扩展[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加上的 IDE**选项**页下**工具**菜单。  
  
 一个对象，实现给定**工具选项**页是与特定 Vspackage 通过关联<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>对象。  
  
 因为环境都实例化实现特定的对象**工具选项**页由 IDE 将显示该特定页：  
  
-   A**工具选项**应实现页，在其自己的对象，而不在实现 VSPackage 的对象。  
  
-   对象不能实现多个**工具选项**页。  
  
## <a name="registering-as-a-tools-options-page-provider"></a>为工具选项页上提供程序注册  
 VSPackage 支持用户配置通过**工具选项**页指示提供这些对象**工具选项**通过应用的实例的页<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>应用于<xref:Microsoft.VisualStudio.Shell.Package>实现。  
  
 必须有的一个实例<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>为每个<xref:Microsoft.VisualStudio.Shell.DialogPage>-派生类型实现**工具选项**页。  
  
 每个实例<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>使用实现的类型**工具选项**页上，包含的类别和子类别用于标识的字符串**工具选项**页上和资源若要注册为提供的类型的信息**工具选项**页。  
  
## <a name="persisting-tools-options-page-state"></a>保留工具选项页状态  
 如果**工具选项**启用自动化支持注册页的实现，IDE 仍然存在页的状态以及所有其他**工具选项**页。  
  
 VSPackage 可以通过使用管理其自己的持久性<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。 应使用只有一个或另一种方法的持久性。  
  
## <a name="implementing-dialogpage-class"></a>实现 DialogPage 类  
 对象，用于提供 VSPackage 的实现<xref:Microsoft.VisualStudio.Shell.DialogPage>-派生的类型可以利用以下继承功能：  
  
-   默认用户界面窗口。  
  
-   一个默认持久性机制可用任一如果<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>应用于类，或者如果<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>属性设置为`true`为<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>，可应用于类。  
  
-   自动化支持。  
  
 一个对象，实现的最低要求**工具选项**页上使用<xref:Microsoft.VisualStudio.Shell.DialogPage>是公共属性的补充。  
  
 如果类正确注册为**工具选项**页上提供程序，然后对其公共属性都位于**选项**部分**工具**菜单中的窗体属性网格。  
  
 可以重写所有这些默认的功能。 例如，若要创建更复杂的用户界面需要仅重写的默认实现<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>。  
  
## <a name="example"></a>示例  
 下面是简单的"你好 world"实现的选项页。 下面的代码添加到默认项目创建的 Visual Studio 包模板使用**菜单命令**选项处于选中状态将充分地演示选项页面功能。  
  
### <a name="description"></a>描述  
 下面的类定义的最小"你好 world"选项页。 打开时，用户可以设置公共`HelloWorld`在属性网格中的属性。  
  
### <a name="code"></a>代码  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>描述  
 将以下特性应用于包类使页上的选项可加载包时。 两个数字是任意资源 Id 的类别和页上，并在结束的布尔值指定该页是否支持自动化。  
  
### <a name="code"></a>代码  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>描述  
 以下事件处理程序显示在选项页中设置的属性值而异的结果。 它使用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>结果方法显式转换为自定义选项页类型，以访问的页面公开的属性。  
  
 对于由包模板生成的项目，调用该函数从`MenuItemCallback`函数以将其附加到的默认命令添加到**工具**菜单。  
  
### <a name="code"></a>代码  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [扩展的用户设置和选项](../../extensibility/extending-user-settings-and-options.md)   
 [选项页的自动化支持](../../extensibility/internals/automation-support-for-options-pages.md)