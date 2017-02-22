---
title: "传统语言服务中的大纲显示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "大纲显示"
  - "以大纲方式显示的语言服务 [托管的包框架]"
  - "大纲显示、 支持的语言服务 [托管的包框架]"
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 传统语言服务中的大纲显示
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以大纲方式显示使可以折叠成概述或大纲复杂的程序。 例如，在 C\# 中的所有方法可以都折叠到单个行中，显示仅方法签名。 此外，结构和类可以折叠以显示仅结构和类的名称。 在单一方法中，可以折叠复杂的逻辑以通过如显示的语句中的，仅第一行中显示的总体流程 `foreach`, ，`if`, ，和 `while`。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要获得详细信息，请参阅 [演练: 大纲显示](../../extensibility/walkthrough-outlining.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 启用支持大纲显示  
 `AutoOutlining` 注册表项设置为 1 以启用自动大纲显示。 自动大纲显示整个源分析当设置加载文件或将其更改，以确定隐藏的区域并显示大纲显示标志符号。 以大纲方式显示也能受手动用户。  
  
 值 `AutoOutlining` 注册表项可以通过获取 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 属性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。`AutoOutlining` 注册表项可以用到一个命名参数初始化 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 属性 \(请参阅 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md) 有关的详细信息\)。  
  
## 隐藏的区域  
 若要提供以大纲方式显示，您的语言服务必须支持隐藏的区域。 这些是文本的的可以展开或折叠范围。 通过标准语言符号，如大括号，或通过自定义的符号，可以分隔隐藏的区域。 例如，C\# 具有 `#region`\/`#endregion` 分隔隐藏的区域的对。  
  
 隐藏的区域管理的隐藏的区域管理器，它公开为 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 接口。  
  
 以大纲方式显示使用隐藏的区域 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> 接口，并在包含隐藏的区域当前可见的状态和标题区范围处于折叠状态时要显示的范围。  
  
 语言服务分析器使用 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法以添加新的隐藏的区域隐藏区域的默认行为时 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 方法允许您自定义外观和行为的轮廓。 一旦隐藏的区域隐藏的区域会话时，会获得 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理语言服务的隐藏的区域。  
  
 如果您需要确定销毁隐藏的区域会话时，隐藏的区域发生更改时，或者您需要确保特定的隐藏的区域可见，则您必须从派生类 <xref:Microsoft.VisualStudio.Package.Source> 类并重写适当的方法， <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, ，<xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, ，和 <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, 分别。  
  
### 示例  
 下面是创建为大括号中的所有成对的隐藏的区域的一个简化的示例。 假定的语言提供了大括号匹配，并且要匹配的大括号至少包括大括号 （{和}）。 这种方法是仅供说明用途。 完整的实现者必须全面的处理中的事例 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>。 此示例还演示如何设置 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 首选项设置为 `true` 暂时。 一种替代方法是指定 `AutoOutlining` 命名参数在 `ProvideLanguageServiceAttribute` 语言包中的属性。  
  
 此示例假定 C\# 注释、 字符串和文字规则。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## 请参阅  
 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)