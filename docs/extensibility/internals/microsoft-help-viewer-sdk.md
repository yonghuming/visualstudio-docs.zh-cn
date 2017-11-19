---
title: "Microsoft 帮助查看器 SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4c676c28b955fac29db5a961f3b566600bcf318
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft 帮助查看器 SDK
本文包含以下任务，以便 Visual Studio 帮助查看器集成商：  
  
-   创建主题 （F1 支持）  
  
-   创建帮助查看器内容品牌包  
  
-   部署一组文章  
  
-   添加到 Visual Studio shell （集成或隔离） 的帮助  
  
-   其他资源  
  
### <a name="creating-a-topic-f1-support"></a>创建主题 （F1 支持）  
本部分概述的组件提供的主题，主题要求、 有关如何创建具有其呈现结果主题 （包括 F1 支持要求） 和最后，示例主题的简短说明。  
  
**帮助查看器主题概述**  
  
当呈现调用主题时，帮助查看器获取与时的安装或上一次更新，以及主题 XHTML，主题相关的品牌包元素，并将组合以生成上提供的内容视图中的两个 (品牌数据 +主题数据）。  品牌包包含徽标、 对内容的行为和品牌文本 （版权，等） 的支持。  下面提供了"创建品牌包"品牌包元素有关的详细信息。  事件没有任何与主题相关联的品牌包，帮助查看器将使用位于帮助查看器应用程序根目录 (Branding_en US.mshc) 中的回退品牌包。  
  
**帮助查看器主题要求**  
  
若要帮助查看器中正确呈现，原始的主题的内容必须是 W3C 基本 1.1 XHTML。  
  
主题通常包含两个部分：  
  
-   元数据 （请参阅内容元数据引用）： 有关主题，例如，主题唯一 ID，主题 TOC ID 的关键字值的数据的父节点 ID，等等。  
  
-   正文内容： 符合 W3C 基本 1.1 XHTML 其中包括支持内容的行为 （可折叠区域、 代码段，等等。完整列表所示）。  
  
Visual Studio 品牌包支持的控件：  
  
-   链接  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   继承的成员  
  
-   LanguageSpecificText  
  
支持的语言字符串 （不区分大小写）：  
  
-   Javascript  
  
-   csharp 或 c#  
  
-   cplusplus 或 visual c + + 或 c + +  
  
-   jscript  
  
-   visualbasic 或 vb  
  
-   f # 或 fsharp 或 fs  
  
-   其他-表示语言名称的字符串  
  
**正在创建帮助查看器主题**  
  
创建名为 ContosoTopic4.htm，新 XHTML 文档并将包含标题标记 （下文）。  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
接下来，添加数据，以定义如何显示 （自助品牌与否），主题是如何若要引用本主题的 F1，本主题在 TOC，其 ID (由其他主题的链接引用） 中存在，等等。请参阅下面有关受支持的元数据的完整列表的"内容元数据"表。  
  
-   在这种情况下，我们将使用我们自己的品牌包，Visual Studio 帮助查看器品牌包的一个变体。  
  
-   添加 F1 元名称和值 ("Microsoft.Help.F1"内容 ="ContosoTopic4")，将匹配 IDE 属性包中提供的 F1 值。  （请参阅 F1 支持部分以了解更多信息。） 这是为 F1 匹配的值在 IDE 时在 IDE 中选择 F1 显示本主题内从调用。  
  
-   添加主题 id。 这是其他主题用于链接到本主题的字符串。  它是本主题的帮助查看器 ID。  
  
-   目录中，将添加本主题的父节点定义此主题 TOC 节点出现的位置。  
  
-   目录中，将添加本主题的节点顺序。 当父节点具有 n 数量的子节点时，定义按子节点的顺序本主题的位置。 例如，本主题是 4 数 4 子主题。)  
  
元数据示例部分：  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
<meta name="SelfBranded" content="false" />     
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
**主题正文**  
  
在主题正文 （不包括页眉和页脚） 将包含页链接、 注意部分、 可折叠区域，代码段中和的语言特定文本部分。  请参阅品牌信息有关的那些区域提供主题的部分。  
  
1.  添加主题标题标记：`<div class="title">Contoso Topic 4</div>`  
  
2.  添加一个部分，请注意：`<div class="alert"> add your table tag and text </div>`  
  
3.  添加的可折叠区域：`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  添加代码片段：`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  添加代码语言特定的文本：`<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />`请注意该 devLangnu = 允许您输入其他语言。 例如，devLangnu ="Fortran"将显示 Fortran 时代码段 DisplayLanguage = Fortran  
  
6.  添加页链接：`<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  注意： 对于不支持新"显示语言"（例如，F #、 Cobol、 Fortran） 代码段中的代码着色将单色。  
  
**示例帮助查看器主题**代码演示了如何定义元数据、 代码段、 可折叠区域和语言特定的文本。  
  
```html
<?xml version="1.0" encoding="utf-8"?>  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
<meta name="SelfBranded" content="false" />     
</head>  
  
<body>  
<div class="title">Contoso Topic 4</div>  
  
  <div id="header">  
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">  
        <tr id="headerTableRow2"><td align="left">  
            <span id="nsrTitle">Contoso Topic 1</span>  
          </td>  
<td align="right">  
</td></tr>  
<tr id="headerTableRow1"><td align="left">  
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>  
          </td></tr>  
      </table>  
</div>  
  
<h2>Table of Contents</h2>  
  
<ul class="toc">  
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>  
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>  
</ul>  
  
<div class="topic">  
  
<div id="mainSection">  
<div id="mainBody">  
  
<a name="introduction"></a>  
<h2>1.0 Introduction</h2>  
<p>[This documentation is for sample purposes only.]</p>  
  
<p>Contoso Topic 1 contains examples of:  
<ul>  
<li>Collapsible Area</li>  
<li>Bookmark ("See also")</li>  
<li>Code Snippets from Branding Package</li>  
</ul>  
 </p>  
<div class="alert"><table><tr><th>  
<strong>Note </strong></th></tr>  
<tr><td>  
<p>This is an example of a <span class="label">Note </span>section.    
Call out important items for your reader in this <span class="label">Note </span>box.  
</p></td></tr>  
</table>  
</div>  
</div>  
  
<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">  
  
            <a id="sectionToggle0"><!----></a>  
  
<div>  
Example of Collapsible Area  
<br/>  
Lorem ipsum dolor sit amet...  
</div>  
</CollapsibleArea>  
  
<div id="snippetGroup" >  
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >  
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip  
Dim messageBoxVB as New System.Text.StringBuilder()  
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)  
    messageBoxVB.AppendLine()  
 ...  
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")  
End Sub  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >  
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)   
{   
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();  
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );  
messageBoxCS.AppendLine();  
...  
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );  
}  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >  
some F# code  
</CodeSnippet>  
</div>  
  
<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />  
  
<a name="seealso"></a>  
<h1 class="heading">See Also</h1>  
  
    <div id="seeAlsoSection" class="section">   
    <div class="seeAlsoStyle">  
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**F1 支持**  
  
在 Visual Studio 中，选择 F1 生成从 IDE 中光标的放置提供值，并填充一个"属性包，"使用提供的值 （基于光标所在的位置。 当光标功能 x 上方时，功能 x 是处于活动状态中/焦点并填充值的属性包。  如果选择了 F1 填充属性包，并且 Visual Studio F1 代码看起来，以查看客户默认帮助源是否为本地或联机 （online 是默认值），然后创建基于用户设置的相应字符串 （online 是默认值） 的命令行程序执行（请参阅帮助管理员指南的 exe 启动参数） 使用本地帮助查看器 + 关键字从本地帮助是否默认情况下或带有参数列表中的关键字的 MSDN URL 的属性包的参数。  
  
如果为 F1 返回三个字符串，引用为多值字符串，使第一个词，查找以便一次点击，如果找到，我们可和;否则，将移动到下一步的字符串。  顺序很重要。 表示法的多值关键字应该是到最短的字符串的最长字符串。  若要验证这一点在的多值关键字的情况下，查看将包括选的关键字的联机 F1 URL 字符串。  
  
在 Visual Studio 2012 中，我们有意之间所做更强的除联机还是脱机，因此，如果用户的设置为 2008，然后我们只需 F1 请求直接传递到我们的联机查询服务 MSDN，而无需通过帮助库代理进行路由我们必须在 Visual Studio 2010。 我们然后依赖于状态的"安装的供应商内容 = true"以确定是否要执行该上下文中的其他内容。 如果为 true，我们再执行此分析和路由的逻辑，具体取决于你想要为您的客户支持。 如果为 false，然后我们只需转到 MSDN。 如果本地用户的设置，然后所有调用只需都转到本地帮助引擎。  
  
F1 流关系图：  
  
![F1 流](../../extensibility/internals/media/f1flow.png "F1flow")  
  
当帮助查看器默认帮助内容源设置为联机 （在浏览器中启动）：  
  
-   Visual Studio 合作伙伴 (VSP) 功能发出到 F1 属性包 （属性包 prefix.keyword 和联机 URL 注册表中找到的前缀） 的值： F1 VSP URL + 参数向浏览器发送。  
  
-   Visual Studio 功能 （语言编辑器，Visual Studio 特定菜单项等）： F1 将 Visual Studio URL 发送到浏览器。  
  
当帮助查看器默认帮助内容源设置为本地帮助 （帮助查看器中启动）：  
  
-   关键字 F1 属性包和本地存储索引之间的匹配位置的 VSP 功能 (也就是说，属性包 prefix.keyword = 本地存储索引中找到的值): F1 呈现帮助查看器中的主题。  
  
-   Visual Studio 功能 （VSP 重写从 Visual Studio 功能发出该属性包没有选项）： F1 呈现帮助查看器中的 Visual Studio 主题。  
  
设置以下注册表值可让 F1 回退供应商的帮助内容。 F1 回退意味着，帮助查看器设置为查找 F1 帮助内容联机，且供应商内容本地安装到用户的硬盘。 帮助查看器应该在本地帮助内容，即使默认设置是联机帮助。  
  
1.  设置**VendorContent**帮助 2.3 注册表项下的值：  
  
    -   对于 32 位操作系统：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent"= dword: 00000001  
  
    -   对于 64 位操作系统：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent"= dword: 00000001  
  
2.  注册帮助 2.3 注册表项下的合作伙伴命名空间：  
  
    -   对于 32 位操作系统：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< 命名空间\>*  
  
         "位置"="脱机"  
  
    -   对于 64 位操作系统：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< 命名空间\>*  
  
         "位置"="脱机"  
  
**基本机 Namespace 分析**  
  
若要打开基本机命名空间分析，请在注册表中添加一个新的 dword 值的名称： BaseNativeNamespaces 并将其值设置为 1 （在下他们想要支持的目录键）。  例如，如果你想要使用 Visual Studio 目录，你无法将密钥添加到路径：  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
当遇到标头/方法的格式中的 F1 关键字时，/ 字符将分析 out，从而导致以下构造：  
  
-   标头： 将是可以用于在注册表中注册的命名空间  
  
-   方法： 这将成为获取传递的关键字。  
  
例如，给定一个名为 CustomLibrary 的自定义库和一个请求传入它 F1 的格式将设置为称为 MyTestMethod，方法`CustomLibrary/MyTestMethod`。  
  
然后，用户可以作为命名空间下的合作伙伴配置单元，注册 CustomLibrary 并提供他们所需的任何位置密钥，传递给查询的关键字将 MyTestMethod。  
  
**启用调试在 IDE 中的工具的帮助**  
  
添加以下注册表项和值：  
  
HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help 键： 零售值中的显示调试输出: 是  
  
在 IDE 中，在帮助菜单项中，选择"调试帮助上下文"  
  
**内容元数据**  
  
下表中，在出现的括号之间的任何字符串是识别的值必须替换为占位符。 例如，在\<元 name="Microsoft.Help.Locale"内容 ="[语言代码]"/ >，"[语言代码]"必须替换为一个值例如"en-我们"。  
  
|属性 （HTML 表示形式）|描述|  
|--------------------------------------|-----------------|  
|\<元 name="Microsoft.Help.Locale"内容 ="[语言代码]"/ >|设置此主题的区域设置。 如果主题中使用此标记，则它必须使用只需一次并且必须高于任何其他 Microsoft 帮助标记插入该域。 如果未使用此标记，通过断字符与该键关联的产品区域设置中，如果指定; 索引主题的正文文本否则为 en-我们使用断字符。 此标记与 ISOC RFC 4646 相符。 若要确保 Microsoft 帮助可正常工作，而不是常规的 Language 特性中使用此属性。|  
|\<元 name="Microsoft.Help.TopicLocale"内容 ="[语言代码]"/ >|此外使用其他区域设置时，请设置此主题的区域设置。 如果主题中使用此标记，则必须使用它只需一次。 当该目录包含多个语言中的内容时，请使用此标记。 在目录中的多个主题可以有相同的 ID，但每个必须指定唯一 TopicLocale。 指定与目录的区域设置匹配 TopicLocale 该主题的内容表中显示的主题。 但是，在搜索结果中显示的主题的所有语言版本。|  
|\<标题 > [标题] \< /t >|指定此主题的标题。 此标记是必需的并且必须使用一个主题中的只是一次。 如果在主题正文不包含标题\<div > 部分中，此标题将显示在的主题以及表中的内容。|  
|\<元名称 ="Microsoft.Help.Keywords"内容 ="[aKeywordPhrase]"/ >|指定一个链接，在帮助查看器的索引窗格中显示的文本。 单击该链接后，将显示主题。你可以指定多个索引关键字主题，或如果您不希望出现在索引中本主题的链接，则可以忽略此标记。 "K"关键字从早期版本的帮助可以转换为此属性。|  
|\<元 name="Microsoft.Help.Id"内容 ="[TopicID]"/ >|设置此主题的标识符。 此标记是必需的并且必须使用一个主题中的只是一次。 ID 必须是唯一的而具有相同的区域设置设置在目录中的主题。 在另一个主题中，可以创建指向此主题的链接，通过使用此 id。|  
|\<元 name="Microsoft.Help.F1"content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|指定此主题的 F1 关键字。 你可以指定多个 F1 关键字主题，或如果您不希望此主题的应用程序用户按下 f1 键时要显示，则可以忽略此标记。 通常情况下，只需一个 F1 关键字指定主题。 "F"关键字从早期版本的帮助可以转换为此属性。|  
|\<元名称 ="Description"content ="[主题说明]"/ >|提供此主题中的内容的简短摘要。 如果主题中使用此标记，则必须使用它只需一次。 此属性可直接通过查询库中;它不存储在索引文件。|  
 元 name="Microsoft.Help.TocParent"内容 ="[parent_Id]"/ >|指定的内容表中的本主题的父主题。 此标记是必需的并且必须使用一个主题中的只是一次。 值是父 Microsoft.Help.Id。 本主题可以只在一个表中的内容的位置。 "-1"被视为 TOC 根的主题 ID。 在[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]，该页是帮助查看器主页。 这是相同的原因，我们专门将 TocParent = 1 添加到一些主题，以确保，它们显示在顶部级别。帮助查看器主页上是系统页并因此非可替换。 如果 VSP 尝试添加 id 为-1 的页，它可能会添加到内容的集，但帮助查看器将始终使用系统页的帮助查看器主页|  
|\<元 name="Microsoft.Help.TocOrder"内容 ="[正整数]"/ >|指定内容的表中本主题显示的位置相对于其对等主题。 此标记是必需的并且必须使用一个主题中的只是一次。 值是一个整数。 指定一个较低值整数主题上方的主题，它指定更高版本值整数。|  
|\<元 name="Microsoft.Help.Product"内容 ="[产品代码]"/ >|指定的产品，本主题介绍。 如果主题中使用此标记，则必须使用它只需一次。 此外可以作为参数传递给帮助索引器提供此信息。|  
|\<元 name="Microsoft.Help.ProductVersion"内容 ="[版本号]"/ >|指定的产品，本主题介绍的版本。 如果主题中使用此标记，则必须使用它只需一次。 此外可以作为参数传递给帮助索引器提供此信息。|  
|\<元 name="Microsoft.Help.Category"内容 ="[string]"/ >|按产品用于标识小节中的内容。 你可以标识多个小节中的主题，或如果您不希望以确定任何小节中的链接，则可以忽略此标记。 此标记用于将属性存储 TargetOS 和 TargetFrameworkMoniker，当一个主题转换从早期版本的帮助。 内容的格式为 AttributeName:AttributeValue。|  
|\<元 name="Microsoft.Help.TopicVersion 内容 ="[主题版本号]"/ >|在目录中存在多个版本时，请指定此版本的主题。 因为 Microsoft.Help.Id 不保证是唯一的多个版本的主题的目录中存在，例如，目录中包含的主题的.NET Framework 3.5 和主题，针对.NET Framework 4 和两个具有相同的 Micro 时此标记时需要软。Help.Id。|  
|\<元名称 ="SelfBranded"content ="[TRUE 或 FALSE]"/ >|指定本主题是使用 Help Library 管理器启动品牌包还是使用特定于主题的品牌包。 此标记必须是 TRUE 或 FALSE。 如果它是 TRUE，则关联的主题的品牌包重写在 Help Library 管理器启动，以便按预期即使它不同于其他内容的呈现呈现主题时设置的品牌包。 如果是 FALSE，根据在 Help Library 管理器启动时设置的品牌包呈现当前主题。 默认情况下，Help Library 管理器假定自助品牌，除非 SelfBranded 变量声明为 TRUE; 否则为 false因此，不需要声明\<元名称 ="SelfBranded"content ="FALSE"/ >。|  
  
### <a name="creating-a-branding-package"></a>创建品牌包  
Visual Studio 版本包含大量不同的 Visual Studio 产品，包括 Visual Studio 合作伙伴的独立和集成的 shell。  每个这些产品需要某种程度的基于主题的帮助内容的品牌支持，唯一的产品。  例如，Visual Studio 主题需要具有一致的品牌演示文稿，而 SQL Studio，包装 ISO Shell，则需要自己唯一帮助内容品牌为每个主题。  集成 Shell 伙伴可能希望其帮助主题，以维护其自己主题品牌时，是在父 Visual Studio 产品帮助内容。  
  
品牌包安装程序包含帮助查看器的产品。  对于 Visual Studio 产品：  
  
-   回退的品牌包 (Branding_\<区域设置 > 能使用.mshc) 安装在帮助查看器 2.3 应用根 (示例： C:\Program Files (x86) \Microsoft Help Viewer\v2.3) 通过帮助查看器语言包。  这适用于不装有品牌包的任何一种产品的情况下 （已安装任何内容） 或其中已安装的品牌包已损坏。  请注意使用应用程序根回退品牌包时，将忽略的 Visual Studio 元素 （徽标和反馈）。  
  
-   从内容包服务安装 Visual Studio 内容时，品牌包也会安装 （适用于第一个时间内容安装方案）。  如果没有对品牌包的更新，更新安装时的下一次的内容更新或其他包安装操作。  
  
Microsoft 帮助查看器支持基于主题元数据的主题的品牌。  
  
-   其中主题元数据定义自助品牌 = true，呈现主题原样，不执行任何操作 （到位品牌）。  
  
-   其中主题元数据定义自助品牌 = false，使用与 TopicVendor 元数据值关联的品牌包。  
  
-   其中主题元数据定义 name="Microsoft.Help.TopicVendor"内容 =\<供应商产品 MSHA 的品牌包名称 >，使用内容的值中定义的品牌包。  
  
-   注意，在 Visual Studio 目录中，没有品牌包的优先级应用程序。  应用第一个 Visual Studio 默认品牌，，然后，如果定义的主题元数据中，并支持相关联的品牌包 （如在安装 msha 中定义），作为替代应用品牌定义的供应商。  
  
品牌元素通常分为三个主要类别：  
  
-   标头元素 （例如反馈链接、 条件免责声明文本、 徽标）  
  
-   内容 （包括展开/折叠控件文本元素的示例数和代码片段元素） 的行为  
  
-   页脚元素 （例如版权所有）  
  
视为品牌化的元素包括的项 （此规范中详细说明）：  
  
-   目录/产品徽标 （例如，Visual Studio）  
  
-   反馈链接和电子邮件元素  
  
-   免责声明文本  
  
-   版权文本  
  
在 Visual Studio 帮助查看器品牌包的支持文件包括：  
  
-   图形 （徽标、 图标，等等。）  
  
-   Branding.js 的脚本文件支持内容的行为  
  
-   Branding.xml-在目录内容之间一致地使用的字符串。  注意： branding.xml 中的 Visual Studio 本地化文本元素包括 _locID ="\<唯一值 >"  
  
-   Branding.css-演示文稿一致性的样式定义  
  
-   Printing.css-一致打印的演示文稿的样式定义  
  
如上所述，品牌包是与主题相关：  
  
-   当 SelfBranded = false 定义的元数据中，主题继承品牌包的目录  
  
-   时，或者当 SelfBranded = false 和那里唯一的品牌包和中定义 MSHA 可用时安装内容  
  
有关实现自定义品牌包的 Vsp (VSP 内容，SelfBranded = True)，继续执行的一种方法是以与回退品牌包 （随一起安装帮助查看器），开始，更改的文件的名称。  Branding_\<区域设置 > 能使用.mshc 文件是用文件扩展名更改为能使用.mshc zip 文件，因此只需从能使用.mshc 扩展名更改为.zip 并提取内容。  请参阅下面有关品牌包元素和修改根据需要 （例如，更改到 VSP 徽标和 Branding.xml 文件中的徽标的引用的徽标，更新 Branding.xml 每 VSP 细节，等等。）。  
  
所有修改都完成后，创建包含所需的品牌元素的 zip 文件，将扩展名更改为能使用.mshc。  
  
若要将自定义品牌包的关联，请创建 MSHA 其中包含对品牌的 mshc 文件和内容的 mshc （包含主题） 的引用。  请参阅下面有关如何创建基本 MSHA"MSHA"。  
  
Branding.xml 文件包含用于一致地呈现一个主题中的特定项，当主题包含一个列表元素\<元 name="Microsoft.Help.SelfBranded"内容 ="false"/ >。  下面列出了 Visual Studio 列表 Branding.xml 文件中的元素。  请注意此列表旨在用于作为模板 ISO Shell 采用者，它们在其中修改这些元素 （例如徽标、 反馈和版权所有） 以满足自己的品牌需求的产品。  
  
注意： 变量"{n}"所具有的代码依赖关系-删除或更改这些值将导致错误和可能是应用程序崩溃。在 Visual Studio 品牌包包含本地化标识符 (示例 _locID="codesnippet.n")。  
  
**Branding.xml**  
  
|||  
|-|-|  
|功能：|**CollapsibleArea**|  
|使用:|展开折叠内容控件文本|  
|**元素**|**值**|  
|ExpandText|Expand|  
|CollapseText|折叠|  
|功能：|**CodeSnippet**|  
|使用:|代码段控件文本。  注意： 具有"非中断"空间的代码段内容将更改为空间中。|  
|**元素**|**值**|  
|CopyToClipboard|复制到剪贴板|  
|ViewColorizedText|着色的视图|  
|CombinedVBTabDisplayLanguage|Visual Basic （示例）|  
|VBDeclaration|声明|  
|VBUsage|用法|  
|功能：|**反馈、 页脚和徽标**|  
|使用:|提供客户提供有关当前通过电子邮件主题的反馈的反馈控件。  版权文本内容。  徽标定义。|  
|**元素**|**值 （这些字符串可以进行修改以满足内容采用需要。）**|  
|版权所有|© 2013 Microsoft Corporation。 保留所有权利。|  
|SendFeedback|\<href ="{0}"{1} > 发送反馈 \< /a > 上本主题的意见。|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|功能：|**免责声明**|  
|使用:|一组的事例特定免责声明机转换内容。|  
|**元素**|**值**|  
|MT_Editable|此文章是由機器翻譯。 如果你有 Internet 连接，选择"查看此主题联机"若要在同一时间在与原始的英语内容的可编辑模式下查看此页。|  
|MT_NonEditable|此文章是由機器翻譯。 如果你有 Internet 连接，选择"查看此主题联机"若要在同一时间在与原始的英语内容的可编辑模式下查看此页。|  
|MT_QualityEditable|本文已手动转换。 如果你有 Internet 连接，选择"查看此主题联机"若要在同一时间在与原始的英语内容的可编辑模式下查看此页。|  
|MT_QualityNonEditable|本文已手动转换。 如果你有 Internet 连接，选择"查看此主题联机"若要在同一时间在与原始的英语内容的可编辑模式下查看此页。|  
|MT_BetaContents|此文章是由機器翻譯的预发行版本。 如果你有 Internet 连接，选择"查看此主题联机"若要在同一时间在与原始的英语内容的可编辑模式下查看此页。|  
|MT_BetaRecycledContents|本文已手动转换为预发布版本。 如果你有 Internet 连接，选择"查看此主题联机"若要在同一时间在与原始的英语内容的可编辑模式下查看此页。|  
|功能：|**LinkTable**|  
|使用:|有关联机主题的链接的支持|  
|**元素**|**值**|  
|LinkTableTitle|链接表|  
|TopicEnuLinkText|查看的英语版本 \< /a > 可在你的计算机本主题。|  
|TopicOnlineLinkText|查看本主题\<href ="{0}"{1} > online \< /a >|  
|OnlineText|Online|  
|功能：|**视频音频控件**|  
|使用:|显示元素和视频内容的文本|  
|**元素**|**值**|  
|MultiMediaNotSupported|必须安装 Internet Explorer 9 或更高版本，以支持 {0} 内容。|  
|VideoText|显示视频|  
|AudioText|流式处理音频|  
|OnlineVideoLinkText|\<p > 若要查看本主题与关联的视频，请单击 {0}\<href ="\ {1 \}"> {2}here\</a >。\</ p >|  
|OnlineAudioLinkText|\<p > 要收听音频与本主题相关联，请单击 {0}\<href ="\ {1 \}"> {2}here\</a >。\</ p >|  
|功能：|**未安装的内容控件**|  
|使用:|使用 contentnotinstalled.htm 在呈现的文本元素 （字符串）|  
|**元素**|**值**|  
|ContentNotInstalledTitle|你的计算机上不发现了任何内容。|  
|ContentNotInstalledDownloadContentText|\<p > 若要将内容下载到你的计算机， \<href ="{0}"{1} > 单击管理选项卡\</a >。\</ p >|  
|ContentNotInstalledText|\<p > 在计算机上安装任何内容。 请参阅您的管理员以本地帮助内容安装。 \< /p >|  
|功能：|**主题找不到控件**|  
|使用:|使用 topicnotfound.htm 在呈现的文本元素 （字符串）|  
|**元素**|**值**|  
|TopicNotFoundTitle|在你的计算机上找不到请求的主题。|  
|TopicNotFoundViewOnlineText|\<p > 你的计算机上找不到您请求的主题，但你可以\<href ="{0}"{1} > 查看联机主题\</a >。\</ p >|  
|TopicNotFoundDownloadContentText|\<p > 请参阅类似主题的链接的导航窗格或\<href ="{0}"{1} > 单击管理选项卡\</a > 以将内容下载到你的计算机。\</ p >|  
|TopicNotFoundText|\<p > 你的计算机上找不到您请求的主题。 \< /p >|  
|功能：|**主题损坏控件**|  
|使用:|使用 topiccorrupted.htm 在呈现的文本元素 （字符串）|  
|**元素**|**值**|  
|TopicCorruptedTitle|无法显示请求的主题。|  
|TopicCorruptedViewOnlineText|\<p > 帮助查看器无法显示请求的主题。 可能有中主题的内容或的基础系统依赖关系的错误。 \< /p >|  
|功能：|**主页上的控件**|  
|使用:|支持帮助查看器的顶级节点内容的显示的文本。|  
|**元素**|**值**|  
|HomePageTitle|帮助查看器主页|  
|HomePageIntroduction|\<p > 欢迎使用 Microsoft Help Viewer，为每个用户使用 Microsoft 工具、 产品、 技术和服务的信息的基本源。 帮助查看器访问你的操作说明和参考信息、 代码示例、 技术文章和的详细信息。 若要查找所需浏览内容的表的内容，使用的全文搜索，或使用关键字的索引的内容中导航。 \< /p >|  
|HomePageContentInstallText|\<p >\<br / > 使用\<href ="{0}"{1} > 管理内容\</a > 选项卡以执行以下操作：\<u l >\<li > 将内容添加到你的计算机。\</ l i / >\<li > 检查你的本地内容的更新。\</ l i / >\<li > 从你的计算机中删除内容。\</ l i / >\<u l > \< /p >|  
|HomePageInstalledBooks|已安装的丛书|  
|HomePageNoBooksInstalled|你的计算机上不发现了任何内容。|  
|HomePageHelpSettings|帮助内容设置|  
|HomePageHelpSettingsText|\<p > 您的当前设置是本地帮助。 帮助查看器显示在你的计算机已安装的内容。\<br / > 若要更改您的源的帮助内容，在 Visual Studio 菜单栏上，选择\<style ="{0}"> 帮助，设置帮助首选项\</>。\<br / > \< /p >|  
|兆字节|MB|  
  
**branding.js**  
  
Branding.js 文件包含由 Visual Studio 帮助查看器品牌元素的 JavaScript。  下面是品牌元素和支持的 JavaScript 函数的列表。  在此文件的顶部的"可本地化的字符串"部分中定义要用于此文件进行本地化的所有字符串。  请注意，已为 branding.js 文件中的本地化字符串创建 ICL 文件。  
  
||||  
|-|-|-|  
|**品牌功能**|**JavaScript 函数**|**描述**|  
|Var...||定义变量|  
|获取用户代码的语言|setUserPreferenceLang|映射索引 # 为代码的语言|  
|设置和获取 cookie 值|getCookie setCookie||  
|继承的成员|changeMembersLabel|展开/折叠继承的成员|  
|当 SelfBranded = False|onLoad|读取要检查其是否打印的请求的查询字符串。  设置所有 codesnippets 集中的用户的首选选项卡。如果它是打印请求将 isPrinterFriendly 设置为 true。 高对比度模式，请检查。|  
|代码段|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|写入到列表的所有可折叠的控件对象。|  
||CA_Click|基于可折叠区域的状态，还定义了哪些图像和文本呈现|  
|徽标的对比度支持|isBlackBackground()|调用以确定是否背景为黑色。  仅准确时在高对比度模式。|  
||isHighContrast()|用彩色的范围检测高对比度模式|  
||onHighContrast(black)|调用时检测到高对比度|  
|LST 功能|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|多媒体功能|标题 （开始，结束时，文本，样式）||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (stylevalue 中的 styleName）||  
||showCC(id)||  
||subtitle(id)||  
  
**HTM 文件**  
  
品牌包中包含一组用于进行通信密钥信息帮助内容的用户，例如主页，其中包含一节介绍了安装哪些内容集和页面告诉用户时主题无法支持方案的 HTM 文件本地组的主题中找到。 请注意这些 HTM 文件可以修改每产品。  ISO Shell 供应商不能够采用默认品牌包并将更改的行为和这些页面的内容为套件它们的需要。  这些文件是指其各自的品牌包顺序品牌的标记来从 branding.xml 文件中获取相应的内容。  
  
||||  
|-|-|-|  
|**文件**|**使用**|**显示的内容源**|  
|homepage.htm|这是一个页，显示当前安装的内容和需要向其内容有关用户显示的任何其他消息。  此文件具有其他的元数据属性"Microsoft.Help.Id"内容 ="-1"会将此内容在本地内容目录的顶部。||  
||< META_HOME_PAGE_TITLE_ADD / >|Branding.xml、 标记\<HomePageTitle >|  
||< HOME_PAGE_INTRODUCTION_SECTION_ADD / >|Branding.xml、 标记\<HomePageIntroduction >|  
||< HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / >|Branding.xml、 标记\<HomePageContentInstallText >|  
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / >|标题部分 Branding.xml 标记\<HomePageInstalledBooks >，从应用程序，生成的数据\<HomePageNoBooksInstalled > 当安装没有书的。|  
||< HOME_PAGE_SETTINGS_SECTION_ADD / >|标题部分 Branding.xml 标记\<HomePageHelpSettings >，部分文本\<HomePageHelpSettingsText >。|  
|topiccorrupted.htm|当主题存在于本地的集中，但由于某种原因无法显示 （已损坏内容）。||  
||< META_TOPIC_CORRUPTED_TITLE_ADD / >|Branding.xml、 标记\<TopicCorruptedTitle >|  
||< TOPIC_CORRUPTED_SECTION_ADD / >|Branding.xml、 标记\<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|当主题中未找到本地内容设置，也不提供联机||  
||< META_TOPIC_NOT_FOUND_TITLE_ADD / >|Branding.xml、 标记\<TopicNotFoundTitle >|  
||< META_TOPIC_NOT_FOUND_ID_ADD / >|Branding.xml、 标记\<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||< TOPIC_NOT_FOUND_SECTION_ADD / >|Branding.xml、 标记\<TopicNotFoundText >|  
|contentnotinstalled.htm|如果已安装了产品没有本地内容。||  
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD / >|Branding.xml、 标记\<ContentNotInstalledTitle >|  
||< META_CONTENT_NOT_INSTALLED_ID_ADD / >|Branding.xml、 标记\<ContentNotInstalledDownloadContentText >|  
||< CONTENT_NOT_INSTALLED_SECTION_ADD / >|Branding.xml、 标记\<ContentNotInstalledText >|  
  
**CSS 文件**  
  
Visual Studio 帮助查看器品牌包包含两个 css 文件，以支持一致 Visual Studio 帮助内容的演示文稿：  
  
-   Branding.css-包含用于呈现位置的 css 元素 SelfBranded = false  
  
-   Printer.css-包含用于呈现位置的 css 元素 SelfBranded = false  
  
Branding.css 文件包括为 Visual Studio 主题演示文稿的定义 (需要注意的是，branding.css 包含在 Branding_\<区域设置 > 能使用.mshc 从包服务可能会更改)。  
  
**图形文件**  
  
Visual Studio 内容显示 Visual Studio 徽标，以及其他图形。  Visual Studio 帮助查看器品牌包中的图形文件的完整列表如下所示。  
  
||||  
|-|-|-|  
|**文件**|**使用**|**示例**|  
|clear.gif|用于呈现可折叠区域||  
|footer_slice.gif|页脚演示文稿||  
|info_icon.gif|显示信息时使用|免责声明|  
|online_icon.gif|此图标将与联机链接关联||  
|tabLeftBD.gif|用于呈现代码段容器||  
|tabRightBD.gif|用于呈现代码段容器||  
|vs_logo_bk.gif|正常的对比度徽标引用 Branding.xml 标记中定义用作\<LogoFileName >。  对于 Visual Studio 产品徽标名称是 vs_logo_bk.gif。||  
|vs_logo_wh.gif|正常的高徽标引用 Branding.xml 标记中定义用作\<LogoFileNameHC >。  对于 Visual Studio 产品徽标名称是 vs_logo_wh.gif。||  
|ccOff.png|隐藏字幕的图形||  
|ccOn.png|隐藏字幕的图形||  
|ImageSprite.png|用于呈现可折叠区域|展开或折叠图形|  
  
### <a name="deploying-a-set-of-topics"></a>部署一的组主题  
这是一个非常简单且快速的教程，用于创建设置由 MSHA 文件和组的 cab 文件的帮助查看器内容部署或 MSHC 包含的主题。 MSHA 是描述一组的 cab 文件的 XML 文件或 MSHC 文件。 帮助查看器可以读取 MSHA 若要获取内容 (列表。CAB 或。MSHC 文件） 可用于本地安装。  
  
这是仅为帮助查看器 MSHA 描述非常基本的 XML 架构入门。  请注意，没有此简要概述下面的示例实现和示例 HelpContentSetup.msha。  
  
此入门，供 MSHA 的名称是的 HelpContentSetup.msha （文件的名称可以是任何内容，其扩展名。MSHA)。 HelpContentSetup.msha （例所示） 应包含 cab 文件或 MSHCs 可用的列表。  请注意，必须一致 MSHA （不支持 MSHA 和 CAB 文件类型的组合） 中的文件类型。 对于每个 CAB 或 MSHC 中，应该有\<v class ="打包">...\</div > （请参阅下面的示例）。  
  
注意： 在下面的实现示例中，我们已提供很多品牌包。 这一点非常重要包括以获取所需的 Visual Studio 内容呈现元素和内容行为。  
  
示例 HelpContentSetup.msha 文件: (将"内容集名称 1"和"内容集 name 2" 等文件名称。)  
  
```html
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>.  
  
```  
  
1.  创建本地文件夹，如下所示"C:\SampleContent"  
  
2.  对于此示例，我们将使用 MSHC 文件以包含主题。  MSHC 是用文件扩展名更改为.zip 从 zip。MSHC。  
  
3.  创建下面为文本文件的 HelpContentSetup.msha （记事本用于创建文件） 并将其保存到的上述设定文件夹 （请参阅步骤 1）。  
  
请注意，"品牌"存在，并且是唯一的类。 品牌 mshc 包括在此入门中，以便安装的内容将具有品牌，并且 MSHCs 中包含的内容行为将品牌包中包含相应的支持元素。 没有它，则系统将查找适用于不属于翻录 （安装） 的支持项内容时，将导致错误。  
  
若要获取 Visual Studio 品牌包，将在 C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ Branding_en US.mshc 文件复制到您的工作文件夹中。  
  
```html  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>  
<div class="package">  
<span class="packageType">branding</span>  
<span class="name">Branding_en-US</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**摘要**  
  
使用和扩展上述步骤将启用 Vsp 将其内容集部署为 Visual Studio 帮助查看器。  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>将帮助添加到 Visual Studio Shell （集成和独立）  
**介绍**  
  
本演练演示如何将帮助内容合并到 Visual Studio Shell 应用程序，然后将其部署。  
  
**要求**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 隔离 Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**概述**  
  
[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell 是的版本[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]IDE 可以基于应用程序。 此类应用程序包含与你创建的扩展一起独立 Shell。 使用独立 Shell 项目模板，其中包含在[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]SDK，可生成扩展。  
  
创建基于独立 Shell 的应用程序和其帮助的基本步骤：  
  
1.  获取[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]ISO Shell 可再发行组件 （Microsoft 下载）。  
  
2.  在 Visual Studio 中，创建基于独立 Shell，例如帮助扩展，在本演练的后面介绍这些 Contoso 帮助扩展。  
  
3.  包装扩展和 ISO Shell 到部署 MSI （应用程序安装程序） 可再发行组件。 本演练不包括设置步骤。  
  
创建 Visual Studio 内容存储。 对于集成外壳方案中，将更改 Visual Studio12 为产品目录名称，如下所示：  
  
-   创建文件夹 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15。  
  
-   创建一个名为 CatalogType.xml 文件并将其添加到的文件夹。 该文件应包含以下代码行：  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
在注册表中定义的内容存储。 集成外壳程序上，将更改为产品目录名称的 VisualStudio15:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     键： LocationPath 字符串值： C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     键： CatalogName 字符串值：[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]文档  
  
**创建项目**  
  
若要创建独立 Shell 扩展：  
  
1.  在 Visual Studio 中，在**文件**，选择**新项目**下**其他项目类型**选择**扩展性**，然后选择**Visual Studio 独立 Shell**。 将项目`ContosoHelpShell`) 创建基于 Visual Studio 独立 Shell 模板扩展性项目。  
  
2.  在解决方案资源管理器，在 ContosoHelpShellUI 项目中，在资源文件文件夹中，打开 ApplicationCommands.vsct。 请确保此行注释掉 （搜索"No_Help"）：`<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  选择 F5 键以编译和运行**调试**。 在独立 Shell IDE 的实验实例中，选择**帮助**菜单。 请确保**视图帮助**，**添加和移除帮助内容**，和**设置帮助首选项**命令显示。  
  
4.  在解决方案资源管理器，在 ContosHelpShell 项目中，在命令行程序自定义文件夹中，打开 ContosoHelpShell.pkgdef。 若要定义 Contoso 帮助目录，添加以下行：  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  在解决方案资源管理器，在 ContosHelpShell 项目中，在命令行程序自定义文件夹中，打开 ContosoHelpShell.Application.pkgdef。 若要启用 F1 帮助，请添加以下行：  
  
    ```  
    // F1 Help Provider  
  
    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="13407"  
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"  
    @="Help3 Provider"  
    [$RootKey$\HelpProviders]  
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"  
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="Help3 Provider"  
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  在解决方案资源管理器，ContosoHelpShell 解决方案的上下文菜单上选择**属性**菜单项。 下**配置属性**，选择**Configuration Manager**。 在**配置**列中，将每个"Debug"的值更改为"发布"。  
  
7.  生成解决方案。 这将创建一组文件在版本文件夹中，将在下一节中使用。  
  
若要测试这就像部署：  
  
1.  在计算机上部署 Contoso，安装下载 （上面） ISO Shell。  
  
2.  中创建一个文件夹\\\Program Files (x86)\\，并将其命名`Contoso`。  
  
3.  将内容复制到 ContosoHelpShell release 文件夹从\\\Program Files (x86) \Contoso\ 文件夹。  
  
4.  启动注册表编辑器，通过选择**运行**中**启动**菜单，然后输入`Regedit`。 在注册表编辑器中，选择**文件**，，然后**导入**。 浏览到 ContosoHelpShell 项目文件夹。 在 ContosoHelpShell 子文件夹中，选择 ContosoHelpShell.reg。  
  
5.  创建内容存储区：  
  
     对于 ISO Shell-创建 Contoso 内容存储 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     有关[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]集成外壳创建文件夹 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  创建 CatalogType.xml 并添加到包含的内容存储 （上一步）：  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  添加以下注册表项：  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath 字符串值：  
  
     ISO shell:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]集成的外壳：  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-美国  
  
     键： CatalogName 字符串值：[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]文档。 对于 ISO Shell，这是你目录的名称。  
  
8.  将你的内容 （cab 或 MSHC 和 MSHA） 复制到本地文件夹。  
  
9. 用于测试内容存储区的示例集成外壳命令行。 ISO shell，更改根据需要以匹配该产品的目录和 launchingApp 值。  
  
     "C:\Program 文件 (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/catalogName VisualStudio15 /helpQuery 方法 ="页 （&) id = ContosoTopic0"/launchingApp Microsoft，visual Studio，12.0  
  
10. 启动 Contoso 应用程序 （从 Contoso 应用程序根目录开始）。 在 ISO 外壳中，选择**帮助**菜单项，并更改**设置帮助首选项**到**使用本地帮助**。  
  
11. 在外壳中，选择**帮助**菜单项，然后**视图帮助**。 应启动本地帮助查看器。 选择“管理内容”选项卡。下**安装源**，选择**磁盘**选项按钮。 选择**...**按钮，然后浏览到包含 （复制到上述步骤中的本地文件夹） 的 Contoso 内容的本地文件夹。 选择 HelpContentSetup.msha。 Contoso 都现在应显示为中的书选择簿中。 选择**添加**，然后选择**更新**按钮 （底部右下角）。  
  
12. Contoso IDE 中，选择 F1 键来测试 F1 功能。  
  
### <a name="additional-resources"></a>其他资源  
对于运行时 API，请参阅[Windows 帮助 API](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)。  
  
有关如何利用帮助 API 的其他信息，请参阅[帮助查看器的代码示例](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
若要提供有关这些组件的反馈，请使用[Microsoft Connect](http://connect.microsoft.com/)。  
  
请将提交到的功能建议[Microsoft 用户之声](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
若要获取更多帮助，请尝试[MSDN 开发人员文档和帮助系统论坛](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
更新的重大问题，请参阅[帮助查看器自述文件](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
若要直接联系帮助查看器 PM 团队，发送到的电子邮件hlpfdbk@microsoft.com