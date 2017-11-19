---
title: "语言服务和编辑器扩展点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c30ed08cc4c62b033f86dfd71e2276bd8be8fbad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="language-service-and-editor-extension-points"></a>语言服务和编辑器扩展点
该编辑器还提供可扩展作为 Managed Extensibility Framework (MEF) 组件部分，包括大多数语言服务功能的扩展点。 主要扩展点类别如下：  
  
-   内容类型  
  
-   分类类型和分类格式  
  
-   边距和滚动条  
  
-   Tags  
  
-   修饰  
  
-   鼠标处理器  
  
-   删除处理程序  
  
-   选项  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>扩展内容类型  
 内容类型是类型的文本，例如由编辑器、"text"、"代码"或"CSharp"的定义。 通过声明类型的变量的定义新的内容类型<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>并向新的内容类型提供一个唯一的名称。 要使用编辑器中注册内容类型，请将其导出以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>是的内容类型的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>是从中派生此内容类型的内容类型的名称。 内容类型可以从多个其他内容的类型继承。  
  
 因为<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>类为密封类，则可以将它导出使用任何类型参数。  
  
 下面的示例显示的内容类型定义导出特性。  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 内容类型可以基于零个或多个预先存在的内容类型。 这些是内置类型：  
  
-   任何： 基本的内容类型。 所有其他内容类型的父级。  
  
-   文本： 非投影内容基本类型。 从"任何"继承。  
  
-   纯文本： 的非代码文本。 继承自"text"。  
  
-   代码： 有关所有类型的代码。 继承自"text"。  
  
-   插入： 将文本从任何类型的处理中排除。 此内容类型的文本再也不会应用于它的任何扩展。  
  
-   投影： 为投影缓冲区的内容。 从"任何"继承。  
  
-   Intellisense： 为 IntelliSense 的内容。 继承自"text"。  
  
-   Sighelp： 签名帮助。 从"intellisense"继承。  
  
-   Sighelp doc： 签名帮助文档。 从"intellisense"继承。  
  
 以下是一些由 Visual Studio 定义的内容类型的一些语言，在 Visual Studio 中托管：  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 若要了解可用的内容类型的列表，导入<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>，并保留编辑器中的内容类型的集合。 下面的代码将此服务作为属性导入。  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 若要将内容类型与文件扩展名相关联，请使用<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>。  
  
> [!NOTE]
>  在 Visual Studio 中，文件扩展名注册使用<xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>上语言服务包。 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>将 MEF 内容类型与文件扩展名已注册这种方式相关联。  
  
 若要导出到的内容类型定义的文件扩展名，必须包括以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>： 指定的文件扩展名。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 指定的内容类型。  
  
 因为<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>类为密封类，则可以将它导出使用任何类型参数。  
  
 下面的示例显示导出特性上的内容类型定义的文件名称扩展。  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>管理文件扩展名和内容类型之间的关联。  
  
## <a name="extending-classification-types-and-classification-formats"></a>扩展分类类型和分类格式  
 分类类型可用于定义你要为其提供不同的处理操作 （例如，着色绿色的"注释"文本和蓝色"关键字"文本） 的文本的类型。 通过声明类型的变量的定义新的分类类型<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>和为其指定唯一名称。  
  
 若要使用的编辑器注册分类类型，请将其导出以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 分类类型的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>： 此分类类型所继承的分类类型的名称。 所有分类类型都继承自"text"，并分类类型可以从多个其他分类类型都继承。  
  
 因为<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>类为密封类，则可以将它导出使用任何类型参数。  
  
 下面的示例显示的分类类型定义导出特性。  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>提供对标准的分类的访问。 内置分类类型包括：  
  
-   “文本”  
  
-   "自然语言"（派生自"text"）  
  
-   "正式语言"（派生自"text"）  
  
-   "字符串"（派生自"文本"）  
  
-   "character"（派生自"文本"）  
  
-   "数字"（派生自"文本"）  
  
 一组的不同错误类型继承自<xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>。 它们包括以下的错误类型：  
  
-   "语法错误"  
  
-   "编译器错误"  
  
-   "其他错误"  
  
-   "警告"  
  
 若要了解可用的分类类型的列表，导入<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>，并保留分类类型集合编辑器。 下面的代码将此服务作为属性导入。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 你可以为新的分类类型定义的分类格式定义。 从派生类<xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition>并将其导出类型<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>一起使用具有以下属性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 的格式的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: 格式的显示名称。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>： 指定是否格式显示在**字体和颜色**页**选项**对话框。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 格式的优先级。 有效值为从<xref:Microsoft.VisualStudio.Text.Classification.Priority>。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>： 分类的名称键入到这种格式映射。  
  
 下面的示例演示根据分类格式定义导出特性。  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 若要发现可用格式的列表，导入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>，并保留编辑器格式的集合。 下面的代码将此服务作为属性导入。  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>扩展边距和滚动条  
 边距和滚动条是除了本身的文本视图编辑器的主视图元素。 你可以提供任意数量的除了文本视图周围出现的标准边距的边距。  
  
 实现<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin>接口可定义边距。 你还必须实现<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>接口可创建边距。  
  
 要使用编辑器中注册的边距提供程序，必须将导出的提供程序以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 边距的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 边距出现，相对于其他边距重叠的顺序。  
  
     这些是内置的页边距：  
  
    -   "Wpf 水平滚动条"  
  
    -   "Wpf 垂直滚动条"  
  
    -   "Wpf 行号边距"  
  
     具有的顺序属性的水平边距`After="Wpf Horizontal Scrollbar"`如下所示的内置边距和具有的顺序属性的水平边距`Before ="Wpf Horizontal Scrollbar"`内置边距的上方显示。 右键具有的顺序属性的垂直边距`After="Wpf Vertical Scrollbar"`滚动条右侧显示。 保留具有的顺序属性的垂直边距`After="Wpf Line Number Margin"`会出现的行号边距的左边 （如果它是可见）。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>： 类型的边距 （左、 右、 顶部或底部）。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 你边距的有效内容 （例如，"text"或"代码"） 的类型。  
  
 下面的示例显示导出特性上的边距提供程序将出现在右侧的行号边距的边距。  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>扩展标记  
 标记是文本的一种将数据与不同类型相关联。 在许多情况下，关联的数据显示为视觉效果，但不是所有标记都的可视化表示形式。 你可以通过实现定义你自己的类型的标记<xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 你还必须实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>提供对于一组给定的文本范围的标记和<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>提供标记器。 你必须导出以及以下特性的标记器提供程序：  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 你的标记的有效内容 （例如，"text"或"代码"） 的类型。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>： 类型的标记。  
  
 下面的示例显示在标记器提供程序上的导出特性。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 以下类型是标记的内置的：  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>： 与关联<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>： 与错误类型关联。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>： 与修饰关联。  
  
    > [!NOTE]
    >  有关的示例<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>，请参阅中的 HighlightWordTag 定义[演练： 突出显示文本](../extensibility/walkthrough-highlighting-text.md)。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>： 与可以展开或折叠在大纲区域相关联。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>： 在文本视图中定义修饰所占用的空间。 有关空间协商修饰的详细信息，请参阅以下部分。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>： 提供自动间距和大小调整为修饰。  
  
 若要查找和使用标记进行缓冲区和视图，导入<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>或<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>，这为你提供<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>的所请求类型。 下面的代码将此服务作为属性导入。  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>标记和 MarkerFormatDefinitions  
 你可以扩展<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>类可以定义一个标记的外观。 必须将导出你的类 (作为<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) 具有以下属性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 用于引用此格式的名称  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>： 这将导致要在 UI 中显示的格式  
  
 在构造函数中，可定义的显示名称和标记的外观。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>定义填充颜色，和<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A>定义的边框颜色。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>是可本地化名称的格式定义。  
  
 下面是格式定义的示例：  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 若要将此格式定义应用于一个标记，引用类 （而不是显示名称） 的名称特性中设置的名称。  
  
> [!NOTE]
>  有关的示例<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>，请参阅中的 HighlightWordFormatDefinition 类[演练： 突出显示文本](../extensibility/walkthrough-highlighting-text.md)。  
  
## <a name="extending-adornments"></a>扩展修饰  
 修饰定义可以为文本视图中显示的文本添加或查看文本本身的视觉效果。 你可以为任何类型的定义你自己修饰<xref:System.Windows.UIElement>。  
  
 在修饰类中，您必须声明<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>。 若要注册修饰层，请将其导出以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 修饰的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 与其他修饰层修饰的顺序。 类<xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers>定义默认的四个层： 选择、 大纲、 插入符号和文本。  
  
 下面的示例演示上修饰层定义导出特性。  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 你必须创建另一个类实现<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>并处理其<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法是实例化修饰的事件。 你必须导出此类以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 此类内容 （例如，"text"或"代码"） 修饰的有效。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>： 此修饰的有效的文本视图的类型。 类<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>具有一组预定义的文本视图角色。 例如，<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>主要用于文本的文件的视图。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>用于在用户可以编辑或使用鼠标和键盘导航的文本视图。 示例<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>视图是编辑器文本视图和**输出**窗口。  
  
 下面的示例演示导出特性修饰提供程序。  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 空间协调修饰是指占用空间在同一级别的文本。 若要创建这种类型的修饰，必须定义继承自标记类<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>，后者定义了修饰所占据的空间量。  
  
 与所有修饰，你必须导出修饰层定义。  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 若要实例化空间协调修饰，必须创建一个类以实现<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，除了实现的类<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>（与其他类型的修饰一样）。  
  
 若要注册的标记器提供程序，必须将其导出以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 你修饰的有效内容 （例如，"text"或"代码"） 的类型。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>： 此文本视图种标记或修饰是否有效。 类<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>具有一组预定义的文本视图角色。 例如，<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>主要用于文本的文件的视图。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>用于在用户可以编辑或使用鼠标和键盘导航的文本视图。 示例<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>视图是编辑器文本视图和**输出**窗口。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>： 类型的标记或已定义的修饰。 你必须添加第二个<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>为<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>。  
  
 下面的示例显示导出特性上的空间协商修饰标记标记器提供程序。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>扩展鼠标处理器  
 你可以添加对的鼠标输入的特殊处理。 创建继承自的类<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>和重写你想要处理的输入的鼠标事件。 你还必须实现<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>中第二个类并将其连同导出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>，指定你的鼠标处理程序的有效内容 （例如，"text"或"代码"） 的类型。  
  
 下面的示例演示在鼠标处理器提供程序上的导出特性。  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>扩展放置处理程序  
 你可以通过创建一个类以实现自定义放置对于特定类型的文本的处理程序的行为<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler>和实现第二个类<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider>创建放处理程序。 你必须导出其放置处理程序以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>： 此放处理程序的有效的文本格式。 按从高到低的优先级顺序处理以下格式：  
  
    1.  任何自定义格式  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  Riff  
  
    6.  差异  
  
    7.  区域设置  
  
    8.  调色板  
  
    9. PenData  
  
    10. 可序列化  
  
    11. SymbolicLink  
  
    12. Xaml  
  
    13. XamlPackage  
  
    14. Tiff  
  
    15. Bitmap  
  
    16. Dib  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. HTML 格式  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Text  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 删除处理程序的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 排序放处理程序之前, 或之后的默认放置处理。 Visual Studio 的默认放置处理名为"DefaultFileDropHandler"。  
  
 下面的示例演示对删除处理程序提供程序的导出特性。  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>扩展编辑器选项  
 你可以定义要仅在一个特定作用域，例如，在文本视图中有效的选项。 该编辑器还提供此组预定义的选项： 编辑器选项、 视图选项和 Windows Presentation Foundation (WPF) 视图选项。 这些选项可在<xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>， <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>，和<xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>。  
  
 若要添加的新选项，请从这些选项定义类之一派生一个类：  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 下面的示例演示如何导出选项定义具有一个布尔值。  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>扩展 IntelliSense  
 IntelliSense 是一组提供有关结构化文本文件的信息的功能的总称和它的语句结束。 这些功能包括语句完成、 签名帮助、 快速信息和电灯泡。 语句结束有助于用户键入正确的语言关键字或成员名称。 签名帮助显示的签名或用户具有刚刚键入的内容的方法的签名。 当鼠标停留在其上时，快速信息将显示类型或成员名称的完整签名。 灯泡提供在某些上下文中，例如，某些标识符已重命名一个匹配项后，重命名的变量的所有匹配项的其他的操作。  
  
 IntelliSense 功能的设计是在所有情况下非常相似：  
  
-   IntelliSense *broker*负责的整个过程。  
  
-   IntelliSense*会话*表示之间的演示程序的顺序或取消所选内容的触发的事件的顺序。 会话通常会触发的某些用户手势。  
  
-   IntelliSense*控制器*负责确定当会话开始时间和结束。 它还决定的信息应该提交和时，应取消会话。  
  
-   IntelliSense*源*提供内容，并确定最佳匹配。  
  
-   IntelliSense*演示器*负责显示内容。  
  
 在大多数情况下，我们建议你提供至少一个源和一个控制器。 如果你想要自定义的显示，你还可以提供演示者。  
  
### <a name="implementing-an-intellisense-source"></a>实现智能感知源  
 若要自定义源，则必须实现一个 （或更多） 的以下源接口：  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>已弃用鉴于<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>。  
  
 此外，你必须实现一种相同类型的提供商：  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>已弃用鉴于<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>。  
  
 你必须导出该提供程序以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 源的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 源适用于的内容 （例如，"text"或"代码"） 的类型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 在其源应显示 （相对于其他源） 的顺序。  
  
-   下面的示例演示在完成源提供程序上的导出特性。  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 有关实现 IntelliSense 源的详细信息，请参阅下面的演练：  
  
 [演练：显示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [演练：显示签名帮助](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [演练：显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>实现智能感知控制器  
 若要自定义控制器，则必须实现<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>接口。 此外，你必须实现控制器提供程序以及以下特性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 控制器的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 控制器适用于的内容 （例如，"text"或"代码"） 的类型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 在该控制器应显示 （相对于其他控制器） 的顺序。  
  
 下面的示例演示在完成控制器提供程序上的导出特性。  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 有关使用 IntelliSense 控制器的详细信息，请参阅下面的演练：  
  
 [演练：显示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)