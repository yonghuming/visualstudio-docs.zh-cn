---
title: "Microsoft 帮助查看器 SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# Microsoft 帮助查看器 SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本文包含以下关于 Visual Studio 帮助查看器集成的任务:  
  
-   创建主题 \(F1 支持\)  
  
-   创建帮助查看器内容品牌包  
  
-   部署一部分的文章  
  
-   添加到 Visual Studio shell \(集成或隔离\) 的帮助  
  
-   其他资源  
  
### 创建主题 \(F1 支持\)  
 本部分概述了组件进行显示的主题，主题要求、 如何创建具有其呈现的结果 \(包括 F1 支持要求\) 的主题和最后，示例主题的简短说明。  
  
 **帮助查看器的主题概述**  
  
 呈现调用某个主题时，帮助查看器获取标记位于安装或上一次更新，以及主题 XHTML 的时间与主题相关联的包元素，并将组合两个导致显示的内容视图 \(标记数据 \+ 主题数据\)。  署名程序包包含徽标、 对内容的行为和署名文字 \(著作权、 等\) 的支持。  请参见"创建品牌包"下面有关标记的包元素的详细信息  事件没有品牌程序包与主题相关联，则帮助查看器将使用位于帮助查看器应用程序根目录 \(Branding\_en US.mshc\) 中的回退署名程序包。  
  
 **帮助查看器主题要求**  
  
 若要帮助查看器中正确呈现，原始的主题的内容必须是 W3C 基本 1.1 XHTML。  
  
 主题通常包含两个部分:  
  
-   元数据 \(请参阅内容元数据引用\): 有关主题，例如，主题唯一 ID，目录 ID 的主题的关键字值的数据的父节点 ID，等等。  
  
-   正文的内容: 符合 W3C 基本 1.1 XHTML 其中包括支持内容的行为 \(可折叠区域、 代码段，等等。完整列表所示\)。  
  
 Visual Studio 品牌包的支持的控件:  
  
-   链接  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   继承的成员  
  
-   LanguageSpecificText  
  
 支持的语言字符串 \(不区分大小写\):  
  
-   javascript  
  
-   csharp 或 c\#  
  
-   cplusplus visualc \+ \+ 或 c \+ \+  
  
-   jscript  
  
-   visual basic 或 vb  
  
-   f \# 或 fsharp 或 f  
  
-   其他 – 表示的语言名称的字符串  
  
 **创建一个帮助查看器的主题**  
  
 创建名为 ContosoTopic4.htm，一个新的 XHTML 文档并包括 title 标记 \(下文\)。  
  
```html  
<html> <head> <title>Contoso Topic 4</title> </head> <body> </body> </html>  
  
```  
  
 接下来，添加数据如何定义主题的方式显示 \(自身品牌与否\)，若要引用本主题的 F1，本主题所在目录中，其 ID \(由其他主题的链接引用\) 中，等等。请参阅下面有关受支持的元数据的完整列表的"内容元数据"表。  
  
-   在这种情况下，我们将使用我们自己署名程序包，Visual Studio 帮助查看器署名程序包的变体。  
  
-   添加 F1 元名和值 \("Microsoft.Help.F1"内容 \="ContosoTopic4"\)，将匹配 IDE 属性包中提供的 F1 值。  \(请参阅 F1 支持部分以了解更多信息。\)   这是与 F1 匹配的值从 IDE 可在 IDE 中选择 f1 键时显示本主题中的调用。  
  
-   添加主题 id。 这是其他主题用于将链接到本主题的字符串。  它是本主题中的帮助查看器 ID。  
  
-   目录中，将添加本主题的父节点，以定义将显示此主题 TOC 节点的位置。  
  
-   目录中，将添加本主题的节点顺序。 当父节点均具有 n，子节点的数目时，定义子节点的顺序本主题的位置。 例如，本主题就是多 4 个 4 子主题。\)  
  
 元数据示例部分:  
  
```html  
<html> <head> <title>Contoso Topic 4</title> <meta name="SelfBranded" content="false" /> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> </head> <body> </body> </html>  
  
```  
  
 **主题正文**  
  
 \(不包括页眉和页脚\) 该主题正文中的将包含页面链接、 注意部分、 可折叠区域、 代码段中和特定语言的文本的某一部分。  请参阅有关的那些区域的显示主题标记部分。  
  
1.  添加主题标题标记:  `<div class="title">Contoso Topic 4</div>`  
  
2.  添加注释部分: `<div class="alert"> add your table tag and text </div>`  
  
3.  添加可折叠区域:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  添加代码段:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  添加代码语言特定的文本:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` 请注意该 devLangnu \= 允许您输入其他语言。 例如，devLangnu \="Fortran"将显示 Fortran 时代码段 DisplayLanguage \= Fortran  
  
6.  添加页面链接: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  注意: 对于不支持新"显示语言"\(例如，F \#、 Cobol、 Fortran\) 代码段中的代码颜色设置将为单色。  
  
 **示例帮助查看器主题** 的代码演示如何定义元数据、 代码段、 可折叠区域和语言特定的文本。  
  
```  
<?xml version="1.0" encoding="utf-8"?> <html> <head> <title>Contoso Topic 4</title> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> <meta name="SelfBranded" content="false" /> </head> <body> <div class="title">Contoso Topic 4</div> <div id="header"> <table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%"> <tr id="headerTableRow2"><td align="left"> <span id="nsrTitle">Contoso Topic 1</span> </td> <td align="right"> </td></tr> <tr id="headerTableRow1"><td align="left"> <span id="runningHeaderText">Contoso Widgets & Sprockets</span> </td></tr> </table> </div> <h2>Table of Contents</h2> <ul class="toc"> <li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li> <li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li> </ul> <div class="topic"> <div id="mainSection"> <div id="mainBody"> <a name="introduction"></a> <h2>1.0 Introduction</h2> <p>[This documentation is for sample purposes only.]</p> <p>Contoso Topic 1 contains examples of: <ul> <li>Collapsible Area</li> <li>Bookmark ("See also")</li> <li>Code Snippets from Branding Package</li> </ul> </p> <div class="alert"><table><tr><th> <strong>Note </strong></th></tr> <tr><td> <p>This is an example of a <span class="label">Note </span>section. Call out important items for your reader in this <span class="label">Note </span>box. </p></td></tr> </table> </div> </div> <CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> <a id="sectionToggle0"><!----></a> <div> Example of Collapsible Area <br/> Lorem ipsum dolor sit amet... </div> </CollapsibleArea> <div id="snippetGroup" > <CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" > Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip Dim messageBoxVB as New System.Text.StringBuilder() messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds) messageBoxVB.AppendLine() ... MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event") End Sub </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e) { System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder(); messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds ); messageBoxCS.AppendLine(); ... MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" ); } </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" > some F# code </CodeSnippet> </div> <h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" /> <a name="seealso"></a> <h1 class="heading">See Also</h1> <div id="seeAlsoSection" class="section"> <div class="seeAlsoStyle"> <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a> </div> </div> </div> </div> </body> </html>  
  
```  
  
 **F1 支持**  
  
 在 Visual Studio 中，选择 f1 键生成提供从 IDE 内的游标的位置的值，并填充一个"属性包"使用提供的值 \(基于光标位置。 当光标上方功能 x 时，功能 x active\/的焦点，并填充值的属性包。  选择 f1 键时填充的属性包以及 Visual Studio F1 代码看起来，以查看客户的默认帮助源是否本地或联机 \(online 是默认值\)，然后创建基于设置的用户的相应字符串 \(online 是默认值\) – 外壳执行 \(请参见帮助管理员指南中有关 exe 启动参数\) 使用本地帮助查看器 \+ 从属性包，如果本地帮助是默认值的关键字的参数或带有在参数列表中的关键字的 MSDN URL。  
  
 如果为 F1 返回了三个字符串，引用要为多值字符串，第一个词，查找为执行一次点击，并且如果找到，我们已完成;否则，将移动到下一个字符串。  顺序很重要。 表示法的多值关键字应该是到最短的字符串的最长字符串。  若要验证这一点在多值的关键字的情况下，查看联机 F1 URL 字符串，这将包括选择的关键字。  
  
 在 Visual Studio 2012 中，我们有意更强的除之间进行联机和脱机，因此，如果用户的设置为 2008，然后我们只需 F1 请求直接传递给我们的在线查询服务 MSDN，而不是通过 Visual Studio 2010 中我们必须帮助库代理进行路由。 我们然后依赖于状态的"安装的供应商内容 \= true"以确定是否要执行该上下文中的其他内容。 如果为 true，我们再执行此分析和路由的逻辑，具体取决于您希望为您的客户支持。 如果为 false，则我们只需转到 MSDN。 如果为本地用户的设置，然后所有调用只需转到本地帮助引擎。  
  
 F1 流关系图:  
  
 ![F1 flow](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 如果帮助查看器的默认帮助内容源设置为联机 \(在浏览器中启动\):  
  
-   Visual Studio 合作伙伴 \(VSP\) 功能发出到 F1 属性包 \(属性包 prefix.keyword 和联机 URL 在注册表中发现的前缀\) 的值: F1 VSP URL \+ 参数向浏览器发送。  
  
-   Visual Studio 功能 \(语言编辑器，Visual Studio 特定菜单项等\): F1 将 Visual Studio URL 发送到浏览器。  
  
 如果帮助查看器的默认帮助内容源设置为本地帮助 \(帮助查看器中启动\):  
  
-   关键字 F1 属性包和本地存储索引之间的匹配位置的 VSP 功能 \(也就是说，属性包 prefix.keyword \= 在本地存储索引中找到的值\): F1 呈现帮助查看器中的主题。  
  
-   Visual Studio 功能 \(VSP 重写从 Visual Studio 功能发出的属性包的任何选项\): F1 呈现帮助查看器中的 Visual Studio 主题。  
  
 设置以下注册表值以便 F1 回退供应商的帮助内容。 F1 回退意味着帮助查看器设置为查找 F1 帮助内容联机，并且供应商内容本地安装到用户的硬盘。 帮助查看器应该查看本地帮助内容即使默认设置是联机帮助。  
  
1.  设置 **VendorContent** 帮助 2.1 注册表项下的值:  
  
    -   对于 32 位操作系统:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent"\= dword: 00000001  
  
    -   对于 64 位操作系统:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent"\= dword: 00000001  
  
2.  注册帮助 2.1 注册表项下的合作伙伴命名空间:  
  
    -   对于 32 位操作系统:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Partner*\\ \< 命名空间 \>*  
  
         "位置"\="脱机"  
  
    -   对于 64 位操作系统:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Partner*\\ \< 命名空间 \>*  
  
         "位置"\="脱机"  
  
 **分析的基础本机命名空间**  
  
 若要打开基本机命名空间解析，请在注册表中添加一个新的 dword 值的名称: BaseNativeNamespaces 并将其值设置为 1 \(在下他们想要支持的目录项\)。  例如，如果您想要使用 Visual Studio 目录，无法将密钥添加到路径中:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
 当标头\/方法遇到了格式的 F1 关键字时，\/ 字符将分析出，从而导致以下构造:  
  
-   标头: 将可用于在注册表中注册的命名空间  
  
-   方法: 这将成为获取传递的关键字。  
  
 例如，给定一个名为 CustomLibrary 的自定义库和一个称为 MyTestMethod，当请求进入 F1 将格式化为方法 `CustomLibrary/MyTestMethod`。  
  
 然后，用户可以为合作伙伴配置单元下, 命名空间注册 CustomLibrary 并提供他们的期望，任何位置密钥并且传递给查询的关键字将 MyTestMethod。  
  
 **启用调试工具在 IDE 中的帮助**  
  
 添加以下注册表项和值:  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\12.0\\Dynamic 帮助键: 显示调试输出在零售值: 是  
  
 在 IDE 中，在帮助菜单项，选择"调试帮助上下文"  
  
 **内容元数据**  
  
 下表中出现的括号之间的任何字符串是一个占位符，必须替换为可识别的值。 例如，在 \< 元 name\="Microsoft.Help.Locale"内容 \="\[语言代码\]"\/ \>，"\[语言代码\]"必须替换由值如"en\-我们"。  
  
|属性 \(HTML 表示形式\)|说明|  
|----------------------|--------|  
|\< 元 name\="Microsoft.Help.Locale"内容 \="\[语言代码\]"\/ \>|设置本主题的区域设置。 如果在主题中使用此标记，则必须在使用它只进行一次并且必须高于任何其他 Microsoft 帮助标记插入该域。 如果未使用此标记，该主题的正文文本索引使用断字符与该键关联的产品区域设置中，如果指定了;否则为 en\-我们使用断字符。 此标记与 ISOC RFC 4646 相符。 若要确保 Microsoft 帮助可正常工作，而不是常规的 Language 特性使用此属性。|  
|\< 元 name\="Microsoft.Help.TopicLocale"内容 \="\[语言代码\]"\/ \>|设置本主题的区域设置时也可使用其他区域设置。 如果在主题中使用此标记，则必须只进行一次使用。 在目录中包含多个语言中的内容时，请使用此标记。 在目录中的多个主题可以有相同的 ID，但每个必须指定唯一 TopicLocale。 指定与目录的区域设置匹配 TopicLocale 的主题已显示在目录中的主题。 但是，在搜索结果中显示的主题的所有语言版本。|  
|\< 标题 \> \[Title\] \< \/ t \>|指定此主题的标题。 此标记是必需的并且必须使用在主题中的只是一次。 如果该主题正文中不包含标题 \< div \> 部分，此标题将显示在主题以及目录中。|  
|\< 元名称 \="Microsoft.Help.Keywords"内容 \="\[aKeywordPhrase\]"\/ \>|指定在帮助查看器的索引窗格中显示的链接的文本。 单击该链接时，会显示的主题。您可以指定多个索引关键字的主题，或如果不希望出现在索引中本主题的链接，则可以忽略此标记。 从早期版本的帮助"K"关键字可以转换为此属性。|  
|\< 元 name\="Microsoft.Help.Id"内容 \="\[TopicID\]"\/ \>|设置本主题的标识符。 此标记是必需的并且必须使用在主题中的只是一次。 ID 必须是唯一的而具有相同的区域设置设置在目录中的主题。 在另一个主题中，可以创建指向本主题的链接，通过使用此 id。|  
|\< 元 name\="Microsoft.Help.F1"content\="\[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator\]"\/ \>|指定此主题的 F1 关键字。 您可以指定多个主题的 F1 关键字或如果不希望应用程序用户按下 f1 键时将会显示本主题，可以忽略此标记。 通常情况下，只是一个 F1 关键字指定某一主题。 从早期版本的帮助的"F"关键字可以转换为此属性。|  
|\< 元名称 \="说明"内容 \="\[主题说明\]"\/ \>|提供了本主题中内容的简短摘要。 如果在主题中使用此标记，则必须只进行一次使用。 通过查询库直接访问此属性它不存储在索引文件。|  
|\< 元 name\="Microsoft.Help.TocParent"内容 \="\[parent\_Id\]"\/ \>|指定目录中本主题的父主题。 此标记是必需的并且必须使用在主题中的只是一次。 值是父级的 Microsoft.Help.Id。 一个主题，可以使用表中的内容的只是一个位置。 "\-1"被视为目录根的主题 ID。 在 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)], ，该网页是帮助查看器主页。 这是我们明确将 TocParent \= 1 添加到这些主题可确保，它们显示在顶部级别相同的原因。帮助查看器主页上是系统页并因此不可替换。 如果尝试添加一个 id 为\-1 页 VSP，它可能会添加到内容集，但帮助查看器将始终使用系统页 – 帮助查看器主页|  
|\< 元 name\="Microsoft.Help.TocOrder"内容 \="\[正整数\]"\/ \>|指定在目录中本主题显示位置相对于其对等主题。 此标记是必需的并且必须使用在主题中的只是一次。 值是一个整数。 指定值较小的整数的主题的主题，它指定较高价值整数上方会出现。|  
|\< 元 name\="Microsoft.Help.Product"内容 \="\[product code\]"\/ \>|指定本主题介绍的产品。 如果在主题中使用此标记，则必须只进行一次使用。 此外可以作为参数传递给帮助索引器提供此信息。|  
|\< 元 name\="Microsoft.Help.ProductVersion"内容 \="\[版本号\]"\/ \>|指定本主题介绍该产品的版本。 如果在主题中使用此标记，则必须只进行一次使用。 此外可以作为参数传递给帮助索引器提供此信息。|  
|\< 元 name\="Microsoft.Help.Category"内容 \="\[string\]"\/ \>|按产品用于标识子节的内容。 您可以标识多个小节的主题，或如果不希望链接以识别任何子节，则可以忽略此标记。 此标记用于 TargetOS 和 TargetFrameworkMoniker 存储属性，当一个主题转换从较早版本的帮助。 内容的格式是 AttributeName:AttributeValue。|  
|\< meta name\="Microsoft.Help.TopicVersion 内容 \="\[主题版本号\]"\/ \>|指定当在目录中有多个版本时，该主题的此版本。 由于 Microsoft.Help.Id 不保证是唯一的因此，当主题的多个版本中存在目录，例如，在目录中包含的主题为.NET Framework 3.5 和主题，针对.NET Framework 4，而且它们都具有相同 Microsoft.Help.Id 时，则需要此标记。|  
|\< 元名称 \="SelfBranded"内容 \="\[TRUE 或 FALSE\]"\/ \>|指定本主题使用 Help Library 管理器启动品牌包或品牌的文件包是特定于主题。 此标记必须是 TRUE 或 FALSE。 如果其值为 TRUE，则关联的主题的署名程序包替代 Help Library 管理器启动，以便按预期即使它不同于其他内容的呈现方式呈现主题时设置的署名程序包。 如果为 FALSE，是根据 Help Library 管理器启动时设置的署名程序包呈现当前主题。 Help Library 管理器默认情况下，假定自品牌，除非 SelfBranded 变量声明为 TRUE; 否则为 false因此，不需要声明 \< 元名称 \="SelfBranded"内容 \="FALSE"\/ \>。|  
  
### 创建品牌包  
 Visual Studio 版本包含许多不同 Visual Studio 产品，包括用于 Visual Studio 合作伙伴的独立和集成的外壳。  这些产品中都需要某种程度的基于主题的帮助内容的品牌支持，唯一的产品。  例如，Visual Studio 主题需要具有一致的品牌演示文稿，而 SQL Studio，包装 ISO Shell，则需要其自己唯一的帮助内容的品牌为每个主题。  集成的命令行程序合作伙伴可能想要在父 Visual Studio 产品的帮助内容，同时维护其自己的主题品牌其帮助主题。  
  
 品牌包安装程序包含帮助查看器中的产品。  对于 Visual Studio 产品:  
  
-   在帮助查看器 2.1 应用程序根目录中安装回退署名程序包 \(Branding\_ \< 区域设置 \> 能使用.mshc\) \(示例: C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\) 通过帮助查看器语言包。  这适用于未安装任一产品品牌包位置的情况下 \(已安装的任何内容\) 或其中已安装的品牌程序包已损坏。  请注意，使用应用程序根回退品牌包时将忽略 Visual Studio 元素 \(徽标和反馈\)。  
  
-   当 Visual Studio 内容安装内容包服务从时，署名程序包也会安装 \(适用于第一次安装内容方案\)。  如果没有对署名程序包的更新，更新安装时的下一次的内容更新或更多文件包安装操作。  
  
 Microsoft 帮助查看器支持基于主题的元数据的主题的品牌。  
  
-   其中主题元数据定义自我品牌 \= true、 呈现主题原样，不执行任何操作 \(尽可能远品牌\)。  
  
-   其中主题元数据定义自我品牌 \= false，使用品牌 TopicVendor 元数据值相关联的包。  
  
-   其中主题元数据定义 name\="Microsoft.Help.TopicVendor"内容 \= \< 供应商 MSHA 中的品牌包名称 \>，使用内容的值中定义的品牌包。  
  
-   请注意，在 Visual Studio 目录，没有主要应用程序的品牌的包。  应用第一个 Visual Studio 默认品牌，，然后，如果主题元数据中定义，并且支持与相关联的品牌程序包 \(在安装 msha 中定义\)，作为替代应用品牌定义的供应商。  
  
 标记元素通常分为三个主要类别:  
  
-   标头元素 \(例如反馈链接、 条件免责声明文本、 徽标\)  
  
-   内容行为 \(示例包括展开\/折叠控件文本元素和代码段元素\)  
  
-   页脚元素 \(例如版权\)  
  
 被视为品牌化的元素中包含的项 \(此规范中详细说明\):  
  
-   目录\/产品徽标 \(例如，Visual Studio\)  
  
-   反馈链接和电子邮件元素  
  
-   免责声明文本  
  
-   版权文本  
  
 Visual Studio 帮助查看器署名程序包中的支持文件包括:  
  
-   \(徽标、 图标等\) 的图形  
  
-   Branding.js – 脚本文件支持内容的行为  
  
-   Branding.xml – 一致地使用目录内容中的字符串。  注意: 对于 branding.xml 中的 Visual Studio 本地化文本元素包含 \_locID \="\< 唯一值 \>"  
  
-   Branding.css – 演示文稿一致性的样式定义  
  
-   Printing.css – 一致打印的演示文稿的样式定义  
  
 如上所述，品牌包都与主题关联:  
  
-   当 SelfBranded \= false 定义的元数据中的主题继承品牌包目录  
  
-   时，或者当 SelfBranded \= false，并且那里唯一的品牌包在 MSHA 和定义可用时安装内容  
  
 有关实现自定义品牌包 Vsp \(VSP 内容，SelfBranded \= True\)，请继续执行的一种方法是开头回退的署名程序包 \(安装帮助查看器\)，并将文件另存为适当的名称更改。  Branding\_ \< 区域设置 \> 能使用.mshc 文件是与文件扩展名更改为能使用.mshc 一个 zip 文件、 因此只需将扩展名从能使用.mshc 更改为.zip 和提取的内容。  请参见下面的品牌包元素并修改视情况而定 \(例如，更改到 VSP 徽标和徽标 Branding.xml 文件中的引用的徽标，Branding.xml 更新每个 VSP 细节，等等。\)。  
  
 当所有修改都已都完成时，创建包含所需的标记元素的 zip 文件，并将扩展名更改为能使用.mshc。  
  
 若要将关联的自定义署名程序包，请创建 MSHA 其中包含对品牌的 mshc 文件和内容的 mshc \(包含主题\) 的引用。  请参阅下面有关如何创建基本 MSHA"MSHA"。  
  
 Branding.xml 文件包含用于一致地呈现某个主题中的特定项时该主题包含一个列表元素 \< 元 name\="Microsoft.Help.SelfBranded"内容 \="false"\/ \>。  下面列出了 Visual Studio Branding.xml 文件中元素的列表。  请注意，该列表旨在用于作为模板 ISO Shell 采纳者，它们在其中修改这些元素 \(例如徽标、 反馈和版权\) 以满足自己产品品牌的需求。  
  
 注意: 标记出"{n}"的变量具有代码依赖项 – 删除或更改这些值将导致错误和可能是应用程序崩溃。Visual Studio 品牌程序包中包含本地化标识符 \(示例 \_locID\="codesnippet.n"\)。  
  
 **Branding.xml**  
  
|||  
|-|-|  
|特色主题:|**CollapsibleArea**|  
|使用:|展开折叠内容控件文本|  
|**元素**|**值**|  
|ExpandText|展开|  
|CollapseText|折叠|  
|特色主题:|**CodeSnippet**|  
|使用:|代码段控件文本。  注意: 具有"无间断"空间的代码段内容将更改为空间中。|  
|**元素**|**值**|  
|CopyToClipboard|复制到剪贴板|  
|ViewColorizedText|查看着色文本|  
|CombinedVBTabDisplayLanguage|Visual Basic \(示例\)|  
|VBDeclaration|声明|  
|VBUsage|用法|  
|特色主题:|**反馈、 页脚和徽标**|  
|使用:|提供为客户提供有关当前通过电子邮件主题的反馈的反馈控件。  版权文本内容。  徽标定义。|  
|**元素**|**值 \(这些字符串可以进行修改以满足内容采纳者需要。\)**|  
|版权|© 2013 Microsoft Corporation。 保留所有权利。|  
|SendFeedback|\< href \="{0}"\\{1\\} \> 有关此主题的 Microsoft 的发送反馈 \<\/a \>。|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]|  
|LogoFileName|vs\_logo\_bk.gif|  
|LogoFileNameHC|vs\_logo\_wh.gif|  
|特色主题:|**免责声明**|  
|使用:|一组事例特定免责声明机翻译内容。|  
|**元素**|**值**|  
|MT\_Editable|此文章由机器翻译。 如果您具有 Internet 连接，选择"联机查看此主题"在同一时间在与原始英文内容的可编辑模式下查看该页。|  
|MT\_NonEditable|此文章由机器翻译。 如果您具有 Internet 连接，选择"联机查看此主题"在同一时间在与原始英文内容的可编辑模式下查看该页。|  
|MT\_QualityEditable|此文章由人工翻译。 如果您具有 Internet 连接，选择"联机查看此主题"在同一时间在与原始英文内容的可编辑模式下查看该页。|  
|MT\_QualityNonEditable|此文章由人工翻译。 如果您具有 Internet 连接，选择"联机查看此主题"在同一时间在与原始英文内容的可编辑模式下查看该页。|  
|MT\_BetaContents|此文章由机器翻译，用于预发行版本。 如果您具有 Internet 连接，选择"联机查看此主题"在同一时间在与原始英文内容的可编辑模式下查看该页。|  
|MT\_BetaRecycledContents|这篇文章由人工翻译的预发行版本。 如果您具有 Internet 连接，选择"联机查看此主题"在同一时间在与原始英文内容的可编辑模式下查看该页。|  
|特色主题:|**LinkTable**|  
|使用:|有关联机主题的链接的支持|  
|**元素**|**值**|  
|LinkTableTitle|链接表|  
|TopicEnuLinkText|查看此主题，它可在您的计算机上的英语版本 \<\/a \>。|  
|TopicOnlineLinkText|查看此主题 \< href \="{0}"\\{1\\} \> 联机 \<\/a \>|  
|OnlineText|联机|  
|特色主题:|**视频的音频控件**|  
|使用:|显示元素和视频内容的文本|  
|**元素**|**值**|  
|MultiMediaNotSupported|必须安装 Internet Explorer 9 或更高版本，以支持 {0} 内容。|  
|VideoText|显示视频|  
|AudioText|流式处理音频|  
|OnlineVideoLinkText|\< p \> 若要查看本主题中，与关联的视频，请单击 {0} \< href \="\\\\ {1 \\\\}"\> \\{2\\}here \<\/a \>。 \<\/p \>|  
|OnlineAudioLinkText|\< p \> 若要收听音频与本主题中，单击 {0} \< href \="\\\\ {1 \\\\}"\> \\{2\\}here \<\/a \>。 \<\/p \>|  
|特色主题:|**未安装的内容控件**|  
|使用:|用于 contentnotinstalled.htm 呈现的文本元素 \(字符串\)|  
|**元素**|**值**|  
|ContentNotInstalledTitle|您的计算机上不找到任何内容。|  
|ContentNotInstalledDownloadContentText|\< p \> 若要将内容下载到您的计算机，\< href \="{0}"\\{1\\} \> 单击管理选项卡 \<\/a \>。 \<\/p \>|  
|ContentNotInstalledText|\< p \> 无内容安装在计算机上。 请与管理员联系本地帮助内容的安装。 \<\/p \>|  
|特色主题:|**主题找不到控件**|  
|使用:|用于 topicnotfound.htm 呈现的文本元素 \(字符串\)|  
|**元素**|**值**|  
|TopicNotFoundTitle|在您的计算机上找不到请求的主题。|  
|TopicNotFoundViewOnlineText|\< p \> 您的计算机上未找到您请求的主题，但您可以 \< href \="{0}"\\{1\\} \> 查看主题联机 \<\/a \>。 \<\/p \>|  
|TopicNotFoundDownloadContentText|\< p \> 请参阅类似主题的链接的导航窗格或 \< href \="{0}"\\{1\\} \> 单击管理选项卡 \<\/a \> 以将内容下载到您的计算机。 \<\/p \>|  
|TopicNotFoundText|\< p \> 您的计算机。 \<\/p \> 上未找到您请求的主题|  
|特色主题:|**主题已损坏的控件**|  
|使用:|用于 topiccorrupted.htm 呈现的文本元素 \(字符串\)|  
|**元素**|**值**|  
|TopicCorruptedTitle|无法显示请求的主题。|  
|TopicCorruptedViewOnlineText|\< p \> 帮助查看器无法显示请求的主题。 可能存在错误的主题的内容或者基础系统依赖项。 \<\/p \>|  
|特色主题:|**主页上的控件**|  
|使用:|支持帮助查看器中的顶级节点内容的显示文本。|  
|**元素**|**值**|  
|HomePageTitle|帮助查看器主页|  
|HomePageIntroduction|\< p \> 欢迎访问 Microsoft 帮助查看器中，为每个用户使用 Microsoft 工具、 产品、 技术和服务的信息的重要途径。 帮助查看器可以访问如何主题和参考信息、 示例代码、 技术文章、 和的详细信息。 若要查找所需浏览目录中的内容，使用全文搜索，或通过使用关键字索引。 \<\/p \> 内容导航|  
|HomePageContentInstallText|\< p \>\< b \/ \> 使用 \< href \="{0}"\\{1\\} \> 管理内容 \<\/a \> 选项卡上，若要执行以下操作: \< u l \>\< i \> 添加的内容分发到您的计算机。 \< \/ \>\< l i \> 检查是否有更新到您本地内容。 \< \/ \>\< l i \> 将内容删除从您的计算机。 \<\/l \/ \>\< l \>\< \/ p \>|  
|HomePageInstalledBooks|已安装的丛书|  
|HomePageNoBooksInstalled|您的计算机上不找到任何内容。|  
|HomePageHelpSettings|帮助内容设置|  
|HomePageHelpSettingsText|\< p \> 您的当前设置为本地帮助。 帮助查看器显示在您的计算机已安装的内容 \< b \/ \> 若要更改您的源的帮助内容，在 Visual Studio 菜单栏上，选择 \< n style \="{0}"\> 帮助，请设置帮助首选项 \< \/ \>。 \< b \/ \>\< \/ p \>|  
|兆字节|MB|  
  
 **branding.js**  
  
 Branding.js 文件包含使用 Visual Studio 帮助查看器标记元素的 JavaScript。  下面是标记元素和支持的 JavaScript 函数的列表。  在此文件的顶部的"可本地化字符串"部分中定义要本地化为此文件的所有字符串。  请注意 ICL 文件已创建的 branding.js 文件中的本地化字符串。  
  
||||  
|-|-|-|  
|**品牌功能**|**JavaScript 函数**|**描述**|  
|Var...||定义变量|  
|获取用户的代码语言|setUserPreferenceLang|将索引映射到代码语言的 \#|  
|设置和获取 cookie 值|getCookie setCookie||  
|继承的成员|changeMembersLabel|展开\/折叠继承的成员|  
|当 SelfBranded \= False|onLoad|读取要检查其是否打印请求的查询字符串。  设置所有 codesnippets 将精力集中用户首选的选项卡。  如果打印请求将 isPrinterFriendly 设置为 true。 检查高对比度模式。|  
|代码段|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|写入到列表中的所有可折叠控件对象。|  
||CA\_Click|基于状态的可折叠区域，还定义了哪些图像和文本呈现|  
|对徽标的对比度支持|isBlackBackground\(\)|调用以确定背景为黑色。  精确时，才在高对比度模式。|  
||isHighContrast\(\)|使用颜色的范围来检测高对比度模式|  
||onHighContrast\(black\)|当检测到高对比度时调用|  
|LST 功能|||  
||addToLanSpecTextIdSet\(id\)||  
||updateLST\(currentLang\)||  
||getDevLangFromCodeSnippet\(lang\)||  
|多媒体功能|标题 \(开始、 结束时，文本样式\)||  
||findAllMediaControls\(normalizedId\)||  
||getActivePlayer\(normalizedId\)||  
||captionsOnOff\(id\)||  
||toSeconds\(t\)||  
||getAllComments\(node\)||  
||styleRectify \(styleName、 styleValue\)||  
||showCC\(id\)||  
||subtitle\(id\)||  
  
 **HTM 文件**  
  
 署名程序包包含一组支持用于关键信息传达给帮助内容的用户，例如主页，其中包含一节介绍了安装哪些内容集和本地组的主题中找不到主题时告诉用户页的方案的 HTM 文件。 请注意这些 HTM 文件，可以修改每个产品。  ISO Shell 供应商就能够采取默认品牌包并将更改的行为和这些页面的内容为套件其需求。  这些文件是指其相应的品牌程序包顺序品牌标记，使其从 branding.xml 文件中获取相应的内容。  
  
||||  
|-|-|-|  
|**文件**|**使用**|**显示内容源**|  
|homepage.htm|这是一个页面，显示当前安装的内容和相应呈现给用户有关其内容的其他任何消息。  此文件具有附加元数据属性"Microsoft.Help.Id"内容 \="\-1"会将此内容在本地内容目录的顶部。||  
||\< META\_HOME\_PAGE\_TITLE\_ADD \/ \>|Branding.xml，标记 \< HomePageTitle \>|  
||\< HOME\_PAGE\_INTRODUCTION\_SECTION\_ADD \/ \>|Branding.xml，标记 \< HomePageIntroduction \>|  
||\< HOME\_PAGE\_CONTENT\_INSTALL\_SECTION\_ADD \/ \>|Branding.xml，标记 \< HomePageContentInstallText \>|  
||\< HOME\_PAGE\_BOOKS\_INSTALLED\_SECTION\_ADD \/ \>|标题部分 Branding.xml 标记 \< HomePageInstalledBooks \> 从应用程序中，\< HomePageNoBooksInstalled \> 安装没有书时生成的数据。|  
||\< HOME\_PAGE\_SETTINGS\_SECTION\_ADD \/ \>|标题 Branding.xml 标记 \< HomePageHelpSettings \> 部分文本 \< HomePageHelpSettingsText \> 一节。|  
|topiccorrupted.htm|如果主题存在于本地设置，但由于某种原因无法显示 \(损坏的内容\)。||  
||\< META\_TOPIC\_CORRUPTED\_TITLE\_ADD \/ \>|Branding.xml，标记 \< TopicCorruptedTitle \>|  
||\< TOPIC\_CORRUPTED\_SECTION\_ADD \/ \>|Branding.xml，标记 \< TopicCorruptedViewOnlineText \>|  
|topicnotfound.htm|当主题中未找到本地内容集，也不提供联机||  
||\< META\_TOPIC\_NOT\_FOUND\_TITLE\_ADD \/ \>|Branding.xml，标记 \< TopicNotFoundTitle \>|  
||\< META\_TOPIC\_NOT\_FOUND\_ID\_ADD \/ \>|Branding.xml、 标记 \< TopicNotFoundViewOnlineText \> \+ \< TopicNotFoundDownloadContentText \>|  
||\< TOPIC\_NOT\_FOUND\_SECTION\_ADD \/ \>|Branding.xml，标记 \< TopicNotFoundText \>|  
|contentnotinstalled.htm|如果已安装了该产品没有本地内容。||  
||\< META\_CONTENT\_NOT\_INSTALLED\_TITLE\_ADD \/ \>|Branding.xml，标记 \< ContentNotInstalledTitle \>|  
||\< META\_CONTENT\_NOT\_INSTALLED\_ID\_ADD \/ \>|Branding.xml，标记 \< ContentNotInstalledDownloadContentText \>|  
||\< CONTENT\_NOT\_INSTALLED\_SECTION\_ADD \/ \>|Branding.xml，标记 \< ContentNotInstalledText \>|  
  
 **CSS 文件**  
  
 Visual Studio 帮助查看器品牌 Package 包含两个 css 文件，以支持一致 Visual Studio 帮助内容的演示文稿:  
  
-   Branding.css – 包含 css 元素用于呈现 where SelfBranded \= false  
  
-   Printer.css – 包含 css 元素用于呈现 where SelfBranded \= false  
  
 Branding.css 文件包括为 Visual Studio 主题演示文稿的定义 \(需要注意的问题是，可能会更改包含在从包服务 Branding\_ \< 区域设置 \> 能使用.mshc branding.css\)。  
  
 **图形文件**  
  
 Visual Studio 内容显示 Visual Studio 徽标，以及其他图形。  下面显示了在 Visual Studio 帮助查看器署名程序包中的图形文件的完整列表。  
  
||||  
|-|-|-|  
|**文件**|**使用**|**示例**|  
|clear.gif|用于呈现可折叠区域||  
|footer\_slice.gif|页脚演示文稿||  
|info\_icon.gif|在显示的信息时使用|免责声明|  
|online\_icon.gif|此图标将是与联机链接相关联||  
|tabLeftBD.gif|用于呈现代码段容器||  
|tabRightBD.gif|用于呈现代码段容器||  
|vs\_logo\_bk.gif|用作普通对比度徽标引用 Branding.xml 标记 \< LogoFileName \> 中定义。  对于 Visual Studio 产品徽标名称是 vs\_logo\_bk.gif。||  
|vs\_logo\_wh.gif|用于以普通高徽标引用，如 Branding.xml 标记 \< LogoFileNameHC \> 中定义。  对于 Visual Studio 产品徽标名称是 vs\_logo\_wh.gif。||  
|ccOff.png|隐藏字幕图||  
|ccOn.png|隐藏字幕图||  
|ImageSprite.png|用于呈现可折叠区域|展开或折叠图形|  
  
### 部署一系列的主题  
 这是非常简单而且快速教程，说明如何创建的设置组成一个 MSHA 文件和 cab 文件的一套帮助查看器内容部署或 MSHC 的包含的主题。 MSHA 是描述一组的 cab 文件的 XML 文件或 MSHC 文件。 帮助查看器可以读取 MSHA 以获取列表的内容 \(。CAB 或。MSHC 文件\) 可用于本地安装。  
  
 这是仅描述最基本的 XML 架构的帮助查看器 MSHA 的入门读物。  请注意，有下面这个简要概述了实现示例和示例 HelpContentSetup.msha。  
  
 此入门指导，供 MSHA 的名称是的 HelpContentSetup.msha \(该文件的名称可以是任何内容，其扩展名。MSHA\)。 HelpContentSetup.msha \(例所示\) 应该包含 MSHCs 可用的 cab 文件的列表。  请注意，必须在 \(不支持 MSHA 和 CAB 文件类型的组合\) MSHA 内一致的文件类型。 对于每个 CAB 或 MSHC，应该有 \< v class \="软件包"\>...\< \/ div \> \(请参阅下面示例中\)。  
  
 注意: 在下面的实现示例，我们包括了署名程序包。 这一点非常重要包括才能获取所需的 Visual Studio 内容呈现使得元素和内容的行为。  
  
 示例 HelpContentSetup.msha 文件: \(替换"内容集名称 1" 和"内容集名称 2" 等使用文件名称。\)  
  
```  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div>.  
  
```  
  
1.  创建本地文件夹，如下所示"C:\\SampleContent"  
  
2.  对于此示例，我们将使用 MSHC 文件包含的主题。  MSHC 是更改，不再是到.zip 扩展名的文件的 zip。MSHC。  
  
3.  创建为文本文件 HelpContentSetup.msha 下面 \(记事本用来创建文件\) 并将其保存到上面记下的文件夹 \(请参阅第 1 步\)。  
  
 请注意，"品牌"存在并且是唯一的类。 品牌 mshc 包含在此初级读本，以便安装的内容将产生的品牌，而 MSHCs 中包含的内容行为署名程序包中包含的相应的支持元素。 没有它，则系统将查找不属于翻录 \(安装\) 的支持项目内容时，将导致错误。  
  
 若要获取 Visual Studio 品牌包，请将位于 C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\\ Branding\_en US.mshc 文件复制到您的工作文件夹。  
  
```html  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div> <div class="package"> <span class="packageType">branding</span> <span class="name">Branding_en-US</span> <span class="deployed">True</span> <a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a> </div> </div> </body> </html>  
  
```  
  
 **摘要**  
  
 使用和扩展上述步骤将启用 Vsp 为 Visual Studio 帮助查看器部署其内容集。  
  
### 将帮助添加到 Visual Studio Shell \(集成和独立\)  
 **介绍**  
  
 本演练演示如何将帮助内容合并到 Visual Studio Shell 应用程序，然后将其部署。  
  
 **要求**  
  
1.  [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 独立 Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **概述**  
  
 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 外壳是一个版本 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] IDE 可基于应用程序。 此类应用程序包含独立的命令行界面以及您创建的扩展。 使用独立 Shell 项目模板，其中包含在 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] SDK 来构建的扩展。  
  
 创建基于独立 Shell 的应用程序和其帮助的基本步骤:  
  
1.  获取 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ISO Shell 可再发行组件 \(Microsoft 下载中心\)。  
  
2.  在 Visual Studio 中创建基于独立 Shell，例如帮助扩展中，在本演练的后面介绍的 Contoso 技术扩展。  
  
3.  包装该扩展和 ISO Shell 成部署 MSI \(应用程序安装程序\) 可再发行组件。 本演练中不包括安装步骤。  
  
 创建 Visual Studio 内容存储区。 对于集成外壳方案中，更改 Visual Studio12 为产品目录名称，如下所示:  
  
-   创建文件夹 C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12。  
  
-   创建一个名为 CatalogType.xml 文件并将其添加到的文件夹。 该文件应包含下面的代码行:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
 在注册表中定义的内容存储。 该集成 Shell 将更改为产品目录名称的 VisualStudio12:  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
     键: LocationPath 字符串值: C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12\\en\-US  
  
     键: CatalogName 字符串值: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 文档  
  
 **创建项目**  
  
 若要创建独立 Shell 扩展:  
  
1.  在 Visual Studio 中，在下 **文件**, ，选择 **新项目**, 下 **其他项目类型** 选择 **扩展性**, ，然后选择  **Visual Studio Shell 独立**。 将项目命名为 `ContosoHelpShell`\) 以创建基于 Visual Studio 独立 Shell 模板的可扩展性项目。  
  
2.  在解决方案资源管理器，在 ContosoHelpShellUI 项目中，在资源文件文件夹中，打开 ApplicationCommands.vsct。 请确保这行注释掉 \(搜索"No\_Help"\): `<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  选择 F5 键以编译并运行 **调试**。 在隔离的 Shell IDE 的实验实例中，选择 **帮助** 菜单。 请确保 **视图帮助**, ，**添加和移除帮助内容**, ，和 **设置帮助首选项** 命令会显示。  
  
4.  在解决方案资源管理器，在 ContosHelpShell 项目中，在命令行程序自定义文件夹中，打开 ContosoHelpShell.pkgdef。 若要定义 Contoso 帮助目录，添加以下行:  
  
    ```  
    [$RootKey$\Help] "Product"="Contoso" "Catalog"="Contoso" “Version"="100" "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  在解决方案资源管理器，在 ContosHelpShell 项目中，在命令行程序自定义文件夹中，打开 ContosoHelpShell.Application.pkgdef。 若要启用 F1 帮助，请添加以下行:  
  
    ```  
    // F1 Help Provider [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="13407" "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}" @="Help3 Provider" [$RootKey$\HelpProviders] @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}" [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="Help3 Provider" @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  在解决方案资源管理器，ContosoHelpShell 解决方案的上下文菜单上选择 **属性** 菜单项。 在下 **配置属性**, ，选择 **Configuration Manager**。 在 **配置** 列中，将每个"Debug"的值更改为"发布"。  
  
7.  生成解决方案。 这将在下一节中使用的发布文件夹中创建一组文件。  
  
 对此进行测试就像部署:  
  
1.  在计算机上正在部署 Contoso，安装下载的 ISO Shell \(之外\)。  
  
2.  \\\\Program Files \(x86\) 中创建一个文件夹 \\，并将其命名 `Contoso`。  
  
3.  ContosoHelpShell 版本文件夹的内容复制到 \\\\Program Files \(x86\) \\Contoso\\ 文件夹中。  
  
4.  启动注册表编辑器，通过选择  **运行** 中 **启动** 菜单，然后输入 `Regedit`。 在注册表编辑器中，选择 **文件**, ，然后 **导入**。 浏览到 ContosoHelpShell 项目文件夹。 在 ContosoHelpShell 子文件夹中，选择 ContosoHelpShell.reg。  
  
5.  创建内容存储区:  
  
     对于 ISO Shell\-创建 Contoso 内容存储 C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\ContosoDev12  
  
     有关 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Integrated Shell，创建文件夹 C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12  
  
6.  创建 CatalogType.xml 并添加到包含的内容存储区 \(上一步\):  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
7.  添加以下注册表项:  
  
     HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12Key: LocationPath 字符串值:  
  
     对于 ISO 外壳:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 集成的 Shell:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\\\en\-US  
  
     键: CatalogName 字符串值: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 文档。 对于 ISO 外壳程序中，这是目录的您的名称。  
  
8.  将您的内容 \(cab 或 MSHC 和 MSHA\) 复制到本地文件夹。  
  
9. 集成外壳的命令行示例测试内容存储区。 ISO 外壳程序中，将更改为适合匹配产品的目录和 launchingApp 值。  
  
     "C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\\HlpViewer.exe"\/catalogName VisualStudio12 \/helpQuery 方法 \="页面和 id \= ContosoTopic0"\/launchingApp Microsoft，visual Studio，12.0  
  
10. 启动 Contoso 应用程序 \(从 Contoso 应用程序根目录开始\)。 在 ISO 外壳中，选择 **帮助** 菜单项和更改 **设置帮助首选项** 到 **使用本地帮助**。  
  
11. 在外壳中，选择 **帮助** 菜单项，然后 **视图帮助**。 本地帮助查看器应该会启动。 选择“管理内容”选项卡。 在下 **安装源**, ，选择 **磁盘** 选项按钮。 选择 **...** 按钮并浏览到包含 Contoso 内容 \(复制到上述步骤中的本地文件夹\) 的本地文件夹。 选择 HelpContentSetup.msha。 Contoso 现在应显示在选择簿书籍。 选择 **添加**, ，然后选择 **更新** 按钮 \(页右下角\)。  
  
12. Contoso IDE 中，选择 F1 键来测试 F1 的功能。  
  
### 其他资源  
 运行时 API，请参阅 [Windows 帮助 API](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)。  
  
 有关如何利用帮助 API 的其他信息，请参阅 [帮助查看器的代码示例](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 若要提供有关这些组件的反馈，请使用 [Microsoft Connect](http://connect.microsoft.com/)。  
  
 请将提交到功能建议 [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 若要获得其他帮助，请尝试 [MSDN 开发人员文档和帮助系统论坛](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 更新的重大问题，请参阅 [帮助查看器自述文件](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 若要直接与帮助查看器 PM 团队联系，向 hlpfdbk@microsoft.com 发送电子邮件