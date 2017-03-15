---
title: "对旧语言服务中的导航栏的支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
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
ms.openlocfilehash: 88636468da333fd9200f8661d88af6e7fdeedc59
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>对旧语言服务中的导航栏的支持
在编辑器视图的顶部导航栏显示文件中的类型和成员。 在左侧的下拉列表，显示类型和成员所示右侧下拉列表。 当用户选择一种类型时，插入符号放置在该类型的第一行中。 当用户选择成员时，插入符号置于该成员的定义。 下拉列表框会更新以反映当前插入符号的位置。  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>显示和更新的导航栏  
 若要支持导航栏中，您必须从派生类<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>类，实现<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 当您的语言服务被授权者提供的代码窗口中，基<xref:Microsoft.VisualStudio.Package.LanguageService>的类实例化<xref:Microsoft.VisualStudio.Package.CodeWindowManager>，其中包含<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>对象，表示代码窗口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CodeWindowManager>对象然后提供一个新<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>对象。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法获取<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 如果返回的一个实例您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>类，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>调用您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法来填充内部列出，并将传递您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象传递给[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下拉栏管理器。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 下拉列表管理器中，条形反过来调用<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>方法您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象以建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>对象，其中包含两个下拉栏。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>  
  
 当插入符号移动时，<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>方法调用<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法。</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> 基<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法会调用<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>要更新的状态的导航栏类</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>中的方法</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A></xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 通过一组<xref:Microsoft.VisualStudio.Package.DropDownMember>对象传递给此方法。</xref:Microsoft.VisualStudio.Package.DropDownMember> 每个对象表示在下拉列表中的项。  
  
## <a name="the-contents-of-the-navigation-bar"></a>导航栏中的内容  
 导航栏通常包含的类型的列表和成员的列表。 类型的列表包括当前的源代码文件中的所有可用的类型。 类型名称包括完整的命名空间信息。 下面是 C# 代码使用两种类型的一个示例︰  
  
```c#  
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
  
 成员列表中显示在类型列表中选择的类型的可用成员。 如果使用上面的代码示例`TestLanguagePackage.TestLanguageService`是为所选的类型成员列表中将包含私有成员`tokens`和`serviceName`。 内部结构`Token`不显示。  
  
 您可以实现使成员名称加粗，当插入符号放在其内部的成员列表。 成员也可以显示中显示为灰色文本，指示它们不在其中插入符号移动当前所在的作用域内。  
  
## <a name="enabling-support-for-the-navigation-bar"></a>启用对导航栏的支持  
 若要启用对导航栏的支持，必须设置`ShowDropdownBarOption`参数<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性设为`true`。</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 此参数设置<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>属性。</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 若要支持导航栏中，必须实现<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>的<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A><xref:Microsoft.VisualStudio.Package.LanguageService>类</xref:Microsoft.VisualStudio.Package.LanguageService>的方法</xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>中的对象</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>  
  
 实现过程中<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法中，如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>属性设置为`true`，您可以返回<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>对象。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 如果未返回对象，将不显示导航栏。  
  
 因此，对于此控件要重置编辑器视图处于打开状态时，可以由用户设置该选项以显示导航栏。 用户必须先关闭然后重新打开编辑器窗口，然后发生更改。  
  
## <a name="implementing-support-for-the-navigation-bar"></a>实现对导航栏的支持  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法采用两个列表 （一个用于每个下拉列表） 和两个值表示每个列表中的当前所选内容。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 中的列表和所选内容值可以更新，在这种情况下<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法必须返回`true`以指示已更改的列表。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
 当所选内容更改时在类型下拉列表，则必须更新成员列表中以反映新的类型。 在成员列表中显示的内容可以是︰  
  
-   当前类型的成员的列表。  
  
-   所有可用的成员源中的文件，但与不在当前类型的所有成员显示在灰显文本。 用户仍可以选择灰显的成员，因此它们可以用于快速导航，但颜色表示它们不是当前所选类型的一部分。  
  
 实现<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法通常执行以下步骤︰</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
1.  获取当前声明的源文件的列表。  
  
     有多种方法来填充的列表。 一种方法是在您的版本上创建一个自定义方法<xref:Microsoft.VisualStudio.Package.LanguageService>类中调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法返回的所有声明的列表的自定义分析原因。</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> 另一种方法可能是通过调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法直接从<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>，原因是自定义分析的方法。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 第三个方法可能是缓存中的声明<xref:Microsoft.VisualStudio.Package.AuthoringScope>类中的最后一个完整分析操作返回<xref:Microsoft.VisualStudio.Package.LanguageService>类，并检索，从<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
2.  填充或更新的类型的列表。  
  
     类型列表的内容可能会以以下方式更新源更改时，或者如果已选择要更改根据当前插入符号位置的类型的文本样式。 请注意，此位置传递到<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
3.  确定要基于当前插入符号位置的类型列表中选择的类型。  
  
     您可以在步骤 1 以查找包含当前插入符号位置的类型中搜索中获取的声明，然后搜索为该类型以确定其索引为类型列表类型列表。  
  
4.  填充或更新的基于所选类型的成员的列表。  
  
     成员列表中反映中当前显示的内容**成员**下拉列表。 成员列表中的内容可能需要更新，如果源已更改，或者如果您要显示只有所选类型的成员，并且所选的类型已更改。 如果您选择要在源文件中显示的所有成员，在列表中每个成员的文本样式将需要在当前所选的类型已被更新。  
  
5.  确定要基于当前插入符号位置的成员列表中选择的成员。  
  
     搜索中获取的声明在步骤 1 中的成员，其中包含当前光标位置，然后搜索为该成员以确定其索引到成员列表中的成员列表。  
  
6.  返回`true`如果到列表或在这两个列表中的选项中进行了任何更改。
