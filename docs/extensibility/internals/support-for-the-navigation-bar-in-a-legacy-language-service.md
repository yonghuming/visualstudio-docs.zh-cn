---
title: "支持旧语言服务中的导航栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 935ea7d9fde2872c952f79afaa95058e9f18d0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>对旧语言服务中的导航栏的支持
在编辑器视图的顶部导航栏显示文件中的类型和成员。 在左侧的下拉列表，显示类型，成员将显示在右侧下拉列表。 当用户选择一种类型时，脱字号位于类型的第一行。 当用户选择成员时，脱字号位于成员的定义。 下拉列表框将更新以反映当前插入符号的位置。  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>显示和更新的导航栏  
 若要支持的导航栏，你必须从派生类<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>类，实现<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。 语言服务时提供的代码窗口中，基<xref:Microsoft.VisualStudio.Package.LanguageService>类实例化<xref:Microsoft.VisualStudio.Package.CodeWindowManager>，其中包含<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>表示代码窗口的对象。 <xref:Microsoft.VisualStudio.Package.CodeWindowManager>对象然后提供一个新<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>对象。 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法获取<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象。 如果返回的实例你<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>类，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>调用你<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法来填充内部列出并传递你<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象传递给[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下拉栏管理器。 下拉栏管理器中，依次调用<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>方法你<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象以建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>对象，其中包含两个下拉栏。  
  
 当脱字号移动时，<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>方法调用<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法。 基<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法调用<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法在你<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>类来更新导航栏的状态。 传递的一组<xref:Microsoft.VisualStudio.Package.DropDownMember>给此方法的对象。 每个对象表示下拉列表中的条目。  
  
## <a name="the-contents-of-the-navigation-bar"></a>导航栏中的内容  
 导航栏通常包含的类型的列表和成员的列表。 类型的列表包括在当前的源文件中的所有可用的类型。 类型名称包含完整的命名空间信息。 下面是 C# 代码使用两种类型的示例：  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 类型列表将显示`TestLanguagePackage.TestLanguageService`和`TestLanguagePackage.TestLanguageService.Tokens`。  
  
 成员列表中显示的类型的类型列表中选择可用的成员。 如果使用上面的代码示例`TestLanguagePackage.TestLanguageService`是选择，则类型成员列表中将包含私有成员`tokens`和`serviceName`。 内部结构`Token`不会显示。  
  
 你可以实现使成员名称加粗，当脱字号位于其内部的成员列表。 成员也可以显示在文本，显示为灰色，指示他们不在当前放置脱字号位置的作用域内。  
  
## <a name="enabling-support-for-the-navigation-bar"></a>启用对导航栏的支持  
 若要启用对导航栏的支持，必须设置`ShowDropdownBarOption`参数<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性设为`true`。 此参数设置 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 属性。 若要支持的导航栏，则必须实现<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象在<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。  
  
 实现中<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法，如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>属性设置为`true`，你可以返回<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象。 如果未返回对象，不会显示导航栏。  
  
 显示导航栏的选项可以设置用户，因此很可能对于此控件的编辑器视图处于打开状态时要重置。 用户必须关闭再重新打开编辑器窗口，然后发生更改。  
  
## <a name="implementing-support-for-the-navigation-bar"></a>实现对导航栏的支持  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法采用两个列表 （一个用于每个下拉列表） 和表示当前选定内容的每个列表中的两个值。 列表和选择值可以更新，在这种情况下<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法必须返回`true`以指示已更改的列表。  
  
 当所选内容更改类型下拉列表中时，必须更新成员列表以反映新的类型。 在成员列表中显示的内容可以是：  
  
-   对于当前的类型的成员的列表。  
  
-   中的所有成员可用源文件，但与不在当前类型的所有成员显示在灰显的文本。 用户仍可以选择灰显的成员，因此它们可以用于快速导航窗格中，但颜色表示它们不是当前所选类型的一部分。  
  
 实现<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法通常会执行以下步骤：  
  
1.  获取当前声明源文件的文件名的列表。  
  
     有多种方式可填充列表。 一种方法是在你的版本上创建的自定义方法<xref:Microsoft.VisualStudio.Package.LanguageService>调用的类<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法返回的所有声明的列表的自定义分析原因。 另一种方法可能是调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法直接从<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>，自定义分析原因的方法。 第三个方法可能是缓存中的声明<xref:Microsoft.VisualStudio.Package.AuthoringScope>类中的最后一个完整分析操作返回<xref:Microsoft.VisualStudio.Package.LanguageService>类和检索，从<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。  
  
2.  填充或更新的类型列表。  
  
     类型列表的内容可能要更新源已更改时，或如果已选择要更改根据当前插入符号位置的类型的文本样式。 请注意，此位置传递给<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。  
  
3.  确定要基于当前插入符号位置的类型列表中选择的类型。  
  
     你可以在步骤 1 到包含当前插入符号位置，类型中搜索中获取的声明，然后搜索该类型到类型列表中确定其索引的类型列表。  
  
4.  填充或更新的基于所选类型的成员的列表。  
  
     成员列表中反映中当前显示的内容**成员**下拉列表。 成员列表中的内容可能需要更新，如果源已更改，或者如果您要显示只有所选类型的成员，并且所选的类型已更改。 如果你选择在源文件中显示的所有成员，然后需要如果当前所选的类型已更改更新列表中每个成员的文本样式。  
  
5.  确定要在基于当前插入符号位置的成员列表中选择的成员。  
  
     搜索中获取的声明在步骤 1 中的成员，其中包含当前插入符号位置，然后搜索该成员，以确定其索引到成员列表中的成员列表。  
  
6.  返回`true`如果到列表或在这两个列表中的选项进行了任何更改。