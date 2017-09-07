---
title: "语法着色旧语言服务在 |Microsoft 文档"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1ec6732b511d437a24149d9cd4b20e593a13a8f0
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>在旧语言服务中的语法着色
语法着色是使不同的一种编程语言中的源文件中不同颜色和样式显示元素的功能。 若要支持此功能，则需要提供分析器或可以识别的词法元素或文件中的标记类型的扫描程序。 许多语言区分关键字、 分隔符 （如括号或大括号），以及注释通过不同的方式对它们进行着色。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解详细信息，请参阅[扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="implementation"></a>实现  
 若要支持着色，托管的包框架 (MPF) 包括<xref:Microsoft.VisualStudio.Package.Colorizer>类，该类实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>接口。 此类与交互<xref:Microsoft.VisualStudio.Package.IScanner>来确定的令牌和颜色。 扫描程序的详细信息，请参阅[旧语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 <xref:Microsoft.VisualStudio.Package.Colorizer>类然后将标记每个字符的颜色信息的标记，并将该信息返回到编辑器中显示的源文件。  
  
 返回到编辑器的颜色信息是元素的可着色项列表的索引。 每个可着色项指定颜色值和一组的字体特性，如粗体或带删除线。 编辑器提供了一组语言服务可以使用的默认着色项。 你需要执行操作的只是指定每个令牌的类型的适当的颜色索引。 但是，你可以为令牌，提供一组自定义可着色项和你提供的索引，并引用而不是默认列表着色项目的列表。 你还必须设置`RequestStockColors`为 0 的注册表项 (或不指定`RequestStockColors`处所有项) 以支持自定义颜色。 你可以设置到一个命名参数与此注册表项<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>用户定义的特性。 有关注册语言服务并设置其选项的详细信息，请参阅[注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)。  
  
## <a name="custom-colorable-items"></a>自定义可着色项  
 若要提供自己的自定义可着色项，必须重写<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>和<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。 第一种方法返回语言服务支持的自定义可着色项的数目和第二个按索引获取着色的自定义项。 创建自定义可着色项的默认列表。 在语言服务的构造函数，你需要做是提供一个名称与每个可着色项。 Visual Studio 自动处理这种情况，其中用户选择一组不同的可着色项。 此名称将会出现在**字体和颜色**上的属性页**选项**对话框 (可从 Visual Studio**工具**菜单) 和确定哪一个此名称用户已重写的颜色。 用户的选择在注册表中缓存中存储和访问按颜色名称。 **字体和颜色**属性页列出了所有的颜色名称按字母顺序，以便可通过使用你语言的名称; 每个颜色名称前组自定义颜色例如，"**TestLanguage 注释**"和"**TestLanguage-关键字**"。 可按类型，你可着色项目进行分组或者"**注释 (TestLanguage)**"和"**关键字 (TestLanguage)**"。 按语言名称分组是首选方法。  
  
> [!CAUTION]
>  强烈建议以避免与现有着色项名称冲突的着色项名称中包括的语言名称。  
  
> [!NOTE]
>  如果在开发过程中更改某个您的颜色的名称，必须重置缓存 Visual Studio 创建第一次访问您的颜色。 你可以通过运行来实现**重置实验性配置单元**从 Visual Studio SDK 程序菜单命令。  
  
 请注意，永远不会引用可着色项列表中的第一项。 Visual Studio 始终提供的默认文本颜色和该项的属性。 与此处理的最简单方法是提供为第一项的占位符着色项。  
  
### <a name="high-color-colorable-items"></a>高颜色着色项  
 可着色项还可以支持通过 24 位或高颜色值<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>接口。 MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>类支持<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>以及正常的颜色的构造函数中指定接口和 24 位颜色。 有关更多详细信息，请参见 <xref:Microsoft.VisualStudio.Package.ColorableItem> 类。 下面的示例演示如何设置关键字和注释的 24 位颜色。 当用户的桌面上; 支持 24 位颜色时，将使用的 24 位色否则，将使用的普通文本颜色。  
  
 请记住，这些是你的语言; 的默认颜色用户可以更改为希望的任意这些颜色。  
  
### <a name="example"></a>示例  
 此示例演示一种方法声明并填充使用的自定义可着色项的数组<xref:Microsoft.VisualStudio.Package.ColorableItem>类。 本示例使用 24 位颜色的关键字和注释颜色。  
  
```csharp  
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
 基<xref:Microsoft.VisualStudio.Package.LanguageService>类具有<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>方法该 instantiantes<xref:Microsoft.VisualStudio.Package.Colorizer>类。 从返回的扫描程序<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法传递给<xref:Microsoft.VisualStudio.Package.Colorizer>类构造函数。  
  
 必须实现<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>你自己的版本中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。 <xref:Microsoft.VisualStudio.Package.Colorizer>类使用扫描仪获取所有令牌的颜色信息。  
  
 扫描程序需要填充<xref:Microsoft.VisualStudio.Package.TokenInfo>结构的每个标记它查找。 此结构包含的信息，如所占据的跨度令牌，颜色索引，若要使用，是哪种类型的令牌，和令牌触发器 (请参阅<xref:Microsoft.VisualStudio.Package.TokenTriggers>)。 仅的范围和颜色索引所需的着色通过<xref:Microsoft.VisualStudio.Package.Colorizer>类。  
  
 颜色索引存储在<xref:Microsoft.VisualStudio.Package.TokenInfo>结构通常是一个介于<xref:Microsoft.VisualStudio.Package.TokenColor>枚举，它提供一定数量的指定索引对应于各种语言元素，如关键字和运算符。 如果你自定义的可着色项列表中的匹配项中提供<xref:Microsoft.VisualStudio.Package.TokenColor>枚举，则你可以仅用作枚举的颜色的每个令牌。 但是，如果你有其他可着色项或者你不想要使用该顺序中的现有值，你可以排列您的自定义可着色项列表，以适应你的需求，并返回到该列表的适当的索引。 只是一定要强制转换到的索引<xref:Microsoft.VisualStudio.Package.TokenColor>存储在时<xref:Microsoft.VisualStudio.Package.TokenInfo>结构;[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]看到仅的索引。  
  
### <a name="example"></a>示例  
 下面的示例演示如何扫描程序可能会识别三种令牌类型： 数字、 标点符号和标识符 （任何不是数字或标点符号）。 此示例是仅供说明用途，并不表示的全面的分析器和扫描程序实现。 它假定`Lexer`类，该类具有`GetNextToken()`返回的字符串的方法。  
  
```csharp  
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
 [旧语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [旧语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)
