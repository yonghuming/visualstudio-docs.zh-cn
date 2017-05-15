---
title: "语法着色早期语言服务在 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b9d98323b3957108746b22702306c9155b142fb9
ms.contentlocale: zh-cn
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>在早期语言服务中的语法着色
语法颜色设置是一种功能，使编程语言在不同的颜色和样式中的源代码文件中显示的不同元素。 若要支持此功能，您需要提供分析器或可以识别的词法元素或多个文件中的令牌类型的扫描程序。 许多语言的着色它们以不同的方式加以区别关键字、 分隔符 （例如圆括号或大括号） 和注释。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要获得详细信息，请参阅[扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="implementation"></a>实现  
 为了支持着色，托管的包框架 (MPF) 包括<xref:Microsoft.VisualStudio.Package.Colorizer>类，该类实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>接口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> </xref:Microsoft.VisualStudio.Package.Colorizer> 此类与交互<xref:Microsoft.VisualStudio.Package.IScanner>来确定令牌和颜色。</xref:Microsoft.VisualStudio.Package.IScanner> 扫描程序的详细信息，请参阅[旧语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 <xref:Microsoft.VisualStudio.Package.Colorizer>类，然后将标记每个字符的标记的颜色信息并将该信息返回到编辑器中显示的源文件。</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 返回到编辑器中的颜色信息是可着色的项的列表中的索引。 每个可着色的项指定颜色值和一组字体属性，如粗体或删除线。 编辑器提供了一套语言服务可以使用的默认可着色项。 您需要做的只是指定每个标记类型的适当的颜色索引。 但是，您可以提供一组自定义可着色的项和您提供的索引对于令牌，并引用您自己的而不是默认列表可着色的项列表。 您还必须设置`RequestStockColors`为 0 的注册表项 (或不指定`RequestStockColors`根本的条目) 以支持自定义颜色。 您可以设置为一个命名参数与此注册表项<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>用户定义的属性。</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 注册语言服务并设置其选项的详细信息，请参阅[注册早期语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)。  
  
## <a name="custom-colorable-items"></a>自定义可着色的项  
 若要提供您自己自定义可着色的项，则必须重写<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>和<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A><xref:Microsoft.VisualStudio.Package.LanguageService>类</xref:Microsoft.VisualStudio.Package.LanguageService>的方法</xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A></xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> 第一种方法返回您的语言服务支持的自定义可着色的项的数目和第二个按索引获取自定义可着色的项。 创建自定义可着色的项的默认列表。 在构造函数中的语言服务，您需要执行是提供一个名称与每个可着色的项。 Visual Studio 自动处理这种情况，其中用户选择一组不同的可着色的项。 此名称就是显示在**字体和颜色**属性页上的**选项**对话框 (可通过 Visual Studio**工具**菜单)，此名称确定哪种颜色的用户已重写。 用户的选择将存储在注册表中的缓存，并通过颜色名称访问。 **字体和颜色**属性页列出了所有的颜色名称按字母顺序，因此您可以通过您的语言名称; 每个颜色名前面放置分组自定义颜色，如"**TestLanguage 注释**"和"**TestLanguage-关键字**"。 可以按类型，您可着色的项进行分组或者"**注释 (TestLanguage)**"和"**关键字 (TestLanguage)**"。 按语言名称的分组是首选方法。  
  
> [!CAUTION]
>  强烈建议可着色的项名称以避免冲突与现有的可着色的项名称中包含该语言的名称。  
  
> [!NOTE]
>  如果您在开发过程中更改其中一个您的颜色的名称，必须重置 Visual Studio 创建了第一次访问了您的颜色的缓存。 您可以执行操作来运行**重置实验室**从 Visual Studio SDK 程序菜单命令。  
  
 请注意，永远不会引用可着色的项列表中的第一项。 Visual Studio 始终提供的默认文本颜色和为该项的属性。 与此处理的最简单方法是提供占位符可着色的项作为第一项。  
  
### <a name="high-color-colorable-items"></a>高颜色可着色的项  
 可着色项还可以支持通过 24 位或高颜色值<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>接口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>类支持<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>正常颜色以及构造函数中指定接口和 24 位颜色。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> </xref:Microsoft.VisualStudio.Package.ColorableItem> 请参阅<xref:Microsoft.VisualStudio.Package.ColorableItem>更多详细信息的类。</xref:Microsoft.VisualStudio.Package.ColorableItem> 下面的示例演示如何设置关键字和注释的 24 位颜色。 在用户的桌面上; 支持 24 位颜色时，将使用 24 位色否则，将使用普通文本颜色。  
  
 请记住，都是您的语言; 的默认颜色用户可以更改为所需的任何这些颜色。  
  
### <a name="example"></a>示例  
 此示例演示如何声明和填充使用<xref:Microsoft.VisualStudio.Package.ColorableItem>类</xref:Microsoft.VisualStudio.Package.ColorableItem>的自定义可着色的项的数组的一种方法 本示例使用 24 位颜色的关键字和注释颜色。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>着色器类和扫描程序  
 基<xref:Microsoft.VisualStudio.Package.LanguageService>类具有<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>方法该 instantiantes<xref:Microsoft.VisualStudio.Package.Colorizer>类</xref:Microsoft.VisualStudio.Package.Colorizer></xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A></xref:Microsoft.VisualStudio.Package.LanguageService> 从返回的扫描程序<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法传递给<xref:Microsoft.VisualStudio.Package.Colorizer>类构造函数。</xref:Microsoft.VisualStudio.Package.Colorizer> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
 您必须实现<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>您自己的<xref:Microsoft.VisualStudio.Package.LanguageService>类</xref:Microsoft.VisualStudio.Package.LanguageService>版本中的方法</xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.Colorizer>类使用扫描仪来获取令牌的颜色的所有信息。</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 扫描程序需要填充<xref:Microsoft.VisualStudio.Package.TokenInfo>结构的每个标记它开始查找。</xref:Microsoft.VisualStudio.Package.TokenInfo> 此结构包含的信息，如该令牌的范围所占颜色索引可以使用，是哪种类型的令牌，和令牌触发器 (请参阅<xref:Microsoft.VisualStudio.Package.TokenTriggers>)。</xref:Microsoft.VisualStudio.Package.TokenTriggers> 只是范围和颜色索引所需的着色的<xref:Microsoft.VisualStudio.Package.Colorizer>类。</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 颜色索引存储在<xref:Microsoft.VisualStudio.Package.TokenInfo>结构通常是一个介于<xref:Microsoft.VisualStudio.Package.TokenColor>枚举，它提供了一定数量的命名对应于各种语言元素，如关键字和运算符的索引。</xref:Microsoft.VisualStudio.Package.TokenColor> </xref:Microsoft.VisualStudio.Package.TokenInfo> 如果您自定义可着色的项列表的匹配项显示时采用<xref:Microsoft.VisualStudio.Package.TokenColor>枚举，则您可以只使用枚举作为颜色为每个标记。</xref:Microsoft.VisualStudio.Package.TokenColor> 但是，如果您有其他可着色的项或不想使用这种顺序中的现有值，您可以排列您的自定义可着色的项列表，以适应您的需求，并将适当的索引返回到该列表。 只需确保对象时将其存储在<xref:Microsoft.VisualStudio.Package.TokenInfo>结构中; 强制转换为<xref:Microsoft.VisualStudio.Package.TokenColor>的索引[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]看到的只是索引。 </xref:Microsoft.VisualStudio.Package.TokenColor></xref:Microsoft.VisualStudio.Package.TokenInfo>  
  
### <a name="example"></a>示例  
 下面的示例演示如何扫描程序可能会识别三种令牌类型︰ 数字、 标点符号和标识符 （任何不是数字或标点符号）。 此示例仅供说明用途，并不代表一个全面的分析器和扫描程序实现。 它假设没有`Lexer`类`GetNextToken()`返回的字符串的方法。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>另请参阅  
 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [注册早期语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)
