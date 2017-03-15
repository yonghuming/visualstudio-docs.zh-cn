---
title: "语言服务和编辑器扩展点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，新的扩展点"
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# 语言服务和编辑器扩展点
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

该编辑器还提供可以扩展为托管可扩展性框架 \(MEF\) 组件部件，包括大多数语言服务功能的扩展点。 主要扩展点类别如下︰  
  
-   内容类型  
  
-   分类类型和分类格式  
  
-   边距和滚动条  
  
-   标记  
  
-   修饰  
  
-   鼠标处理器  
  
-   拖放处理程序  
  
-   选项  
  
-   IntelliSense  
  
## 扩展内容类型  
 内容类型是文本，例如由编辑器、"text"、"代码"或"CSharp"类型的定义。 通过声明类型的变量来定义新的内容类型 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> ，并为新内容类型提供一个唯一的名称。 要使用编辑器中注册内容类型，请将其导出与下列属性一起使用︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 是的内容类型的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> 是从中派生此内容类型的内容类型的名称。 内容类型可以从多个内容类型继承。  
  
 因为 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 类为密封类，则可以将它导出不使用任何类型参数。  
  
 下面的示例演示上的内容类型定义导出特性。  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 内容类型可以基于零个或多个预先存在的内容类型。 以下是内置类型︰  
  
-   任意︰ 基本内容类型。 所有其他内容类型的父级。  
  
-   文本︰ 非投影内容基本类型。 从"any"继承。  
  
-   纯文本︰ 对于非代码的文本。 继承自"text"。  
  
-   代码︰ 用于所有类型的代码。 继承自"text"。  
  
-   插入︰ 从任何类型的处理中排除该文本。 此内容类型的文本将永远不必对其应用任何扩展。  
  
-   投影︰ 为投影缓冲区的内容。 从"any"继承。  
  
-   智能感知︰ 用于智能感知的内容。 继承自"text"。  
  
-   Sighelp︰ 签名帮助。 从"intellisense"继承。  
  
-   Sighelp doc︰ 签名帮助文档。 从"intellisense"继承。  
  
 以下是一些由 Visual Studio 定义的内容类型以及一些 Visual Studio 中托管的语言︰  
  
-   Basic  
  
-   C\/C\+\+  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F\#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 若要发现可用的内容类型的列表，导入 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, ，并保留编辑器中的内容类型的集合。 下面的代码将此服务导入为一个属性。  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 若要将内容类型与文件扩展名关联，请使用 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>。  
  
> [!NOTE]
>  在 Visual Studio 中，文件扩展名通过使用已注册 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> 语言服务包。<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 将 MEF 内容类型与已以这种方式注册的文件扩展名相关联。  
  
 若要对该内容类型定义导出的文件扩展名，必须包括以下特性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>︰ 指定的文件扩展名。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 指定的内容类型。  
  
 因为 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 类为密封类，则可以将它导出不使用任何类型参数。  
  
 下面的示例演示上文件扩展名与内容类型定义导出特性。  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> 管理文件扩展名和内容类型之间的关联。  
  
## 扩展分类类型和分类设置格式  
 分类类型可用于定义要提供不同的处理操作 （例如，着色"关键字"蓝色"注释"文字和绿色） 文本的类型。 通过将声明类型的变量定义新的分类类型 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 并为其提供一个唯一的名称。  
  
 要使用编辑器中注册的分类类型，请将其导出与下列属性一起使用︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 此分类类型的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>︰ 此分类类型所继承的分类类型的名称。 所有分类类型都继承自"text"，并且分类类型可能都继承自多个其他分类类型。  
  
 因为 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 类为密封类，则可以将它导出不使用任何类型参数。  
  
 下面的示例演示在分类类型定义导出特性。  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> 提供对标准的分类的访问。 内置的分类类型包括︰  
  
-   “文本”  
  
-   "自然语言"（从"text"派生而来）  
  
-   "正式语言"（从"text"派生而来）  
  
-   "string"（从"文本"派生而来）  
  
-   "character"（从"文本"派生而来）  
  
-   "数字"（从"文本"派生而来）  
  
 一组不同的错误类型继承自 <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>。 它们包括以下的错误类型︰  
  
-   "语法错误"  
  
-   "编译器错误"  
  
-   "其他错误"  
  
-   "警告"  
  
 若要发现可用的分类类型的列表，导入 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, ，并保留编辑器中的分类类型的集合。 下面的代码将此服务导入为一个属性。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 您可以定义分类格式定义为新的分类类型。 从派生类 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> 并将其导出的类型 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, 一起使用具有以下属性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 格式的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>︰ 格式的显示名称。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>︰ 指定是否在上将显示该格式 **字体和颜色** 页 **选项** 对话框。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 格式的优先级。 有效值为从 <xref:Microsoft.VisualStudio.Text.Classification.Priority>。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>︰ 这种格式映射到类型分类的名称。  
  
 下面的示例演示在分类格式定义导出特性。  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 若要发现可用的格式的列表，导入 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, ，并保留的格式为编辑器中的集合。 下面的代码将此服务导入为一个属性。  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## 扩展的边距和滚动条  
 边距和滚动条是除了本身的文本视图编辑器的主视图元素。 您可以提供任意数量的除了文本视图周围出现的标准边距的边距。  
  
 实现 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> 接口来定义边距。 此外必须实现 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 接口，以创建边距。  
  
 若要将边距提供程序注册编辑器中，必须将导出提供程序和以下属性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 边距的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 边距出现，相对于其他边距重叠的顺序。  
  
     这些是内置的页边距︰  
  
    -   "Wpf 水平滚动条"  
  
    -   "Wpf 垂直滚动条"  
  
    -   "Wpf 行号边距"  
  
     有顺序的属性的水平边距 `After="Wpf Horizontal Scrollbar"` 如下所示的内置边距和有顺序的属性的水平边距 `Before ="Wpf Horizontal Scrollbar"` 显示上方的内置边距。 右键有顺序的属性的垂直边距 `After="Wpf Vertical Scrollbar"` 右侧的滚动条显示。 留有顺序的属性的垂直边距 `After="Wpf Line Number Margin"` 显示行号边距的左侧，（如果可见）。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>︰ 这种边距 （左、 右、 顶部或底部）。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 你边距的有效内容 （例如，"text"或"代码"） 的类型。  
  
 下面的示例显示导出特性上的边距提供程序显示在右侧的行号边距的边距。  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## 扩展标记  
 标记是文本的一种方法将数据与不同类型相关联。 在许多情况下，关联的数据显示为视觉效果，但并不是所有标记都有可视化表示形式。 您可以通过实现定义您自己的类型的标记 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 此外必须实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 提供对于一组给定的文本范围的标记和 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 提供标记。 必须导出与下列属性一起使用的标记提供程序︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 你的标记的有效内容 （例如，"text"或"代码"） 的类型。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>︰ 类型的标记。  
  
 下面的示例演示导出特性标记提供程序上。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 以下几种标记是内置的︰  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>︰ 与关联 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>︰ 与错误类型相关联。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>︰ 与使用修饰相关联。  
  
    > [!NOTE]
    >  以举例说明 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, ，请参阅中的 HighlightWordTag 定义 [演练 ︰ 突出显示文本](../extensibility/walkthrough-highlighting-text.md)。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>︰ 与可展开或折叠的大纲显示中的区域相关联。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>︰ 在文本视图中定义使用修饰所占用的空间。 有关空间协调修饰的详细信息，请参阅下一节。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>︰ 提供自动调整间距和大小的修饰。  
  
 若要查找和使用的缓冲区和视图的标记，导入 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> 或 <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, ，它为您提供 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 所请求的类型。 下面的代码将此服务导入为一个属性。  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### 标记和 MarkerFormatDefinitions  
 您可以扩展 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 类可以定义标记的外观。 必须导出您的类 \(作为 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>\) 具有以下属性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 用于引用此格式的名称  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>︰ 这将导致要在 UI 中显示的格式  
  
 在构造函数中，您定义的显示名称和标记的外观。<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 定义填充颜色和 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> 定义的边框颜色。<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> 格式定义的可本地化名称。  
  
 下面是格式定义的示例︰  
  
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
>  以举例说明 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, ，请参阅中的 HighlightWordFormatDefinition 类 [演练 ︰ 突出显示文本](../extensibility/walkthrough-highlighting-text.md)。  
  
## 扩展修饰  
 修饰定义可添加到在文本视图中显示的文本或对文本视图自身中的视觉效果。 您可以为任何类型的定义您自己修饰 <xref:System.Windows.UIElement>。  
  
 在修饰类中，您必须声明 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>。 若要注册修饰层，请将其导出与下列属性一起使用︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 修饰的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 与其他修饰层修饰的顺序。 此类 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 定义了四个默认层︰ 所选内容、 大纲显示、 插入符号和文本。  
  
 下面的示例演示在修饰层定义导出特性。  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 您必须创建一个实现的第二个类 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 并处理其 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 通过实例化修饰的事件。 必须导出此类以及以下属性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 此类内容 （例如，"text"或"代码"） 修饰的有效。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>︰ 此修饰的有效的文本视图的种类。 此类 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 应具有的预定义的文本视图角色集。 例如， <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 主要用于文件的文本视图。<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 适用于文本视图，用户可以编辑或通过使用鼠标和键盘导航。 示例 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 视图是编辑器文本视图和 **输出** 窗口。  
  
 下面的示例演示导出特性修饰提供程序。  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 空间协调修饰是一种占用空间在同一级别的文本。 若要创建这种类型的修饰，必须定义标记类，该类继承 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, ，它定义修饰占用的空间量。  
  
 与所有修饰，则必须导出修饰层定义。  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 若要实例化空间协调修饰，必须创建一个类以实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ，除了实现的类 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> （与其他类型的修饰一样）。  
  
 若要注册的标记提供程序，必须将其导出与下列属性一起使用︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 你修饰的有效内容 （例如，"text"或"代码"） 的类型。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>︰ 此文本视图的类型标记或修饰是否有效。 此类 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 应具有的预定义的文本视图角色集。 例如， <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 主要用于文件的文本视图。<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 适用于文本视图，用户可以编辑或通过使用鼠标和键盘导航。 示例 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 视图是编辑器文本视图和 **输出** 窗口。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>︰ 类型的标记或已定义的修饰。 您必须添加第二个 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 为 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>。  
  
 下面的示例演示导出特性上的空间协调修饰标记的标记提供程序。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## 扩展鼠标处理器  
 您可以添加对鼠标输入的特殊处理。 创建一个类，继承自 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> 并重写要处理的输入的鼠标事件。 此外必须实现 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> 在第二个类并将其与导出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ，指定您的鼠标处理程序的有效内容 （例如，"text"或"代码"） 的类型。  
  
 下面的示例演示鼠标处理器提供程序上的导出特性。  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## 扩展拖放处理程序  
 您可以通过创建一个类以实现自定义拖放处理程序对特定类型的文本的行为 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> 和实现的第二个类 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> 创建拖放处理程序。 必须导出与下列属性一起使用的拖放处理程序︰  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>︰ 此拖放处理程序的有效的文本格式。 按从最高到低的优先级顺序处理采用以下格式︰  
  
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
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 拖放处理程序的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 排序放处理程序之前, 或之后在默认的拖放处理程序。 Visual Studio 默认拖放处理程序被命名为"DefaultFileDropHandler"。  
  
 下面的示例演示在拖放处理程序提供程序上的导出特性。  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## 扩展编辑器选项  
 您可以定义仅在某些作用域，例如，在文本视图中有效的选项。 该编辑器还提供这一套预定义的选项︰ 编辑器选项、 视图选项和 Windows Presentation Foundation \(WPF\) 视图选项。 这些选项可以找到在 <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, ，<xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, ，和 <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>。  
  
 若要添加一个新的选项，请从这些选项定义类之一派生一个类︰  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 下面的示例演示如何将导出选项定义具有一个布尔值。  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## 扩展 IntelliSense  
 IntelliSense 是用于一组功能提供了有关结构化文本的信息的常用术语和适用于该语句结束。 这些功能包括语句完成、 签名帮助、 快速信息和电灯泡。 语句结束有助于用户键入的语言关键字或成员名称正确无误。 签名帮助显示的签名或签名的方法的用户只需键入。 当鼠标停留在其上时，快速信息将显示的类型或成员名称的完整签名。 灯泡图标提供其他操作在某些上下文中，例如，某些标识符在重命名一个匹配项之后重命名的变量的所有匹配项。  
  
 智能感知功能的设计是在所有情况下非常相似︰  
  
-   IntelliSense *broker* 负责整个过程。  
  
-   IntelliSense *会话* 表示之间的表示器的顺序或取消所选内容的触发的事件序列。 通常由某些用户笔势触发该会话。  
  
-   IntelliSense *控制器* 负责决定当会话开始时间和结束。 它还决定的信息应该已提交和会话时应被取消。  
  
-   IntelliSense *源* 提供内容并确定最佳匹配项。  
  
-   IntelliSense *演示者* 负责显示内容。  
  
 在大多数情况下，我们建议您提供至少一个源和一个控制器。 如果您想要自定义的显示，还可以提供演示者。  
  
### 实现智能感知源  
 若要自定义源，必须实现一个 （或以上） 以下源接口︰  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 已弃用倾向于采用 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>。  
  
 此外，您必须实现同一种类的提供程序︰  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 已弃用倾向于采用 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>。  
  
 必须导出提供程序和以下属性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 源的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 此类内容 （例如，"text"或"代码"） 源适用。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 源应 （相对于其他源） 的显示的顺序。  
  
-   下面的示例显示导出特性上完成源提供程序。  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 有关实现智能感知源的详细信息，请参阅下面的演练︰  
  
 [演练︰ 显示快速信息工具提示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)  
  
 [演练︰ 显示签名帮助](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [演练: 显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### 实现智能感知控制器  
 若要自定义控制器，则必须实现 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> 接口。 此外，您必须实现与下列属性一起使用的控制器提供程序︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 控制器的名称。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 此类内容 （例如，"text"或"代码"） 控制器适用。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 在控制器应 （相对于其他控制器） 的显示的顺序。  
  
 下面的示例显示导出特性上完成 controller 提供程序。  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 有关使用 IntelliSense 控制器的详细信息，请参阅下面的演练︰  
  
 [演练︰ 显示快速信息工具提示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)