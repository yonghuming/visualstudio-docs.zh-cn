---
title: "演练: 实现代码段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练: 实现代码段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以创建代码段，并将它们包括在编辑器扩展，以便该扩展的用户可以将它们添加到其自己的代码。  
  
 代码段是一段代码或其他可以合并在一个文件中的文本。 若要查看已在为特定的编程语言中注册的所有代码段 **工具** 菜单上，单击 **代码片段管理器**。 若要插入代码段，在文件中，右键单击要代码片段中，请单击 **插入代码段** 或 **外侧代码**, 、 找到所需的代码段，然后双击它。 按 TAB 或 SHIFT \+ TAB 修改代码段的相关部分，然后按 ENTER 或 esc 键来接受它。 有关详细信息，请参阅[代码段](../ide/code-snippets.md)。  
  
 代码段包含在具有.snippet 文件扩展名的 XML 文件中。 代码段可以包含，以便用户可以查找和更改其插入代码段后将突出显示的字段。 代码段文件还提供信息 **代码片段管理器** ，以便它可以在正确的类别中显示代码段名称。 有关代码段架构信息，请参阅 [代码段架构参考](../ide/code-snippets-schema-reference.md)。  
  
 本演练介绍如何完成这些任务:  
  
1.  创建并注册为特定语言的代码段。  
  
2.  添加 **插入代码段** 命令的快捷菜单。  
  
3.  实现代码段扩展。  
  
 本演练基于 [演练: 显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
## 系统必备  
 若要执行本演练中，必须安装 Visual Studio SDK。 有关更多信息，请参见[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 创建和注册代码段  
 通常情况下，代码段是与已注册的语言服务相关联。 但是，不需要实现 <xref:Microsoft.VisualStudio.Package.LanguageService> 注册代码段。 相反，只需在代码段索引文件中指定一个 GUID，然后使用相同 GUID 的计算机中 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 添加到您的项目。  
  
 以下步骤演示如何创建代码段，并将其与特定 GUID 关联。  
  
1.  创建以下目录结构:  
  
     **%InstallDir%\\TestSnippets\\Snippets\\1033\\**  
  
     其中 *%installdir%* 是 Visual Studio 安装文件夹。 \(虽然此路径通常用来安装代码段，您可以指定任何路径\)。  
  
2.  \\1033\\ 文件夹中创建的.xml 文件，并将其命名 **TestSnippets.xml**。 \(尽管此名称通常用于代码段索引文件，您可以指定任何名称，只要具有文件扩展名为.xml。\) 添加以下文本，然后删除占位符 GUID 并添加您自己。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  在代码段文件夹中创建一个文件，将其 **测试**`.snippet`, ，然后添加以下文本:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 下列步骤显示如何注册的代码段。  
  
#### 若要为特定 GUID 注册代码段  
  
1.  打开 **CompletionTest** 项目。 有关如何创建此项目的信息，请参阅 [演练: 显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
2.  在项目中，添加对下列程序集的引用:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml 进行比较  
  
3.  在项目中，打开 source.extension.vsixmanifest 文件。  
  
4.  请确保 **资产** 选项卡包含 **VsPackage** 内容类型，且 **项目** 设置为项目的名称。  
  
5.  选择 CompletionTest 项目，然后在属性窗口中设置 **生成 Pkgdef 文件** 到 **true**。 保存项目。  
  
6.  添加静态 `SnippetUtilities` 类传递给该项目。  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  在 SnippetUtilities 类中，将 GUID 定义，并为其提供 SnippetsIndex.xml 文件中使用的值。  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  添加 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 到 `TestCompletionHandler` 类。 此属性可以添加到项目中的任何公共或内部 \(非静态\) 类。 \(你可能需要添加 `using` Microsoft.VisualStudio.Shell 命名空间的语句。\)  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. 生成并运行该项目。 在启动时运行该项目的 Visual Studio 的实验实例中，您只需注册的代码段应显示在 **代码片段管理器** 下 **TestSnippets** 语言。  
  
## 添加到快捷菜单插入代码段命令  
 **插入代码段** 命令中未包括的文本文件的快捷菜单。 因此，您必须启用该命令。  
  
#### 若要添加到快捷菜单插入代码段命令  
  
1.  打开 `TestCompletionCommandHandler` 类文件。  
  
     因为此类实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, ，您可以激活 **插入代码段** 命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法。 启用命令之前，请检查，这种方法不被称为自动化函数内部因为时 **插入代码段** 单击命令，则会显示代码段选择器用户界面 \(UI\)。  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  生成并运行该项目。 在实验实例中，打开具有.zzz 文件扩展名的文件，然后右键单击任意位置中。**插入代码段** 命令应出现在快捷菜单。  
  
## 在代码段选择器 UI 中实现的代码段扩展  
 本部分演示如何实现代码段扩展，以使代码段选择器用户界面时，所显示 **插入代码段** 快捷方式菜单中单击。 当用户类型的代码段快捷方式，然后按选项卡上，也会扩展代码段。  
  
 若要显示代码段选择器用户界面并进行导航和后插入代码片段接受，请使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 插入操作本身由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。  
  
 代码段扩展该实现使用旧 <xref:Microsoft.VisualStudio.TextManager.Interop> 接口。 当从当前的编辑器类转换为旧代码时，请记住，旧式界面使用行号和列号的组合可以在文本缓冲区中，指定位置但当前类使用一个索引。 因此，如果缓冲区中具有每个都有 10 个字符的三行 \(加上一个换行符，计为 1 个字符\)，第三个行的第四个字符位于位置 27 在当前实现中，但它位于第 2 行，则位置 3 中以前的实现。  
  
#### 若要实现的代码段扩展  
  
1.  对包含文件 `TestCompletionCommandHandler` 类中，添加以下 `using` 语句。  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  使 `TestCompletionCommandHandler` 类实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 接口。  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  在 `TestCompletionCommandHandlerProvider` 类中，导入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>。  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  添加代码扩展接口一些私有字段和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  构造函数中 `TestCompletionCommandHandler` 类中，设置以下字段。  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  若要显示代码段选择器，当用户单击 **插入代码段** 命令，添加以下代码到 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 \(若要使此说明更具可读性，exec \(\) 用于语句完成不显示代码; 相反，将代码块添加到现有的方法。\) 检查存在的字符的代码后面添加下面的代码块。  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  如果一个代码段具有可定位的字段，扩展会话将保持打开状态，直到显式接受扩展;如果该代码段不具有任何字段，该会话已关闭，并且作为返回 `null` 通过 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> 方法。 在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法，代码段选择器在上一步中添加的用户界面代码之后添加以下代码以处理段导航 \(当用户在插入代码段后按 TAB 或 SHIFT \+ TAB\)。  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  若要插入代码段，当用户类型对应的快捷方式，然后按选项卡上，将代码添加到 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 插入代码段的私有方法将在后面的步骤所示。 在上一步中添加的导航代码后面添加下面的代码。  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. 实现的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 接口。 在此实现中，感兴趣的唯一方法是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>。 其他方法应只返回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. 实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。 将在稍后的步骤中介绍用于实际将扩展的帮助器方法。<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 提供行和列信息，你可以从获取 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. 以下 private 方法插入代码段中，根据该快捷方式或根据标题和路径。 然后，它调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> 与该代码段的方法。  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## 构建和测试代码段扩展  
 您可以测试是否段扩展适用于您的项目。  
  
1.  生成解决方案。 在调试器中运行此项目时，Visual Studio 的第二个实例进行实例化。  
  
2.  打开一个文本文件，并键入一些文本。  
  
3.  在文本中的任意位置右键单击，然后单击 **插入代码段**。  
  
4.  代码段选取器的 UI 应显示带有弹出式窗口，指出 **测试替换字段**。 双击弹出的窗口中。  
  
     应插入以下代码段。  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     不要按 ENTER 或 esc 键。  
  
5.  按 tab 键和 SHIFT \+ TAB 切换"第一个"和"第二个"之间。  
  
6.  按 ENTER 或 esc 键以接受插入。  
  
7.  在文本的不同部件中，键入"测试"，然后按 tab 键。 由于"test"的代码段快捷方式，应再次插入代码段。  
  
## 后续步骤