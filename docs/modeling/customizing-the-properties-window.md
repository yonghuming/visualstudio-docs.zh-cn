---
title: "自定义“属性”窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, “属性”窗口"
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 20
caps.handback.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 自定义“属性”窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以自定义属性窗口的外观和行为在域特定语言 \(DSL\)中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  在 DSL 定义，则定义在每个域类的字段的特性。  默认情况下，那么，当您选择类的实例，请在关系图或模型资源管理器中，每个字段属性窗口列表。  由此可以查看和编辑字段的特性的值，因此，即使您尚未映射它们在建模图的字段。  
  
## 名称、说明和类别  
 **名称和显示名称**。  在字段的特性的定义，属性的显示名称是显示在 " 属性 " 窗口中的运行时的名称。  相反，名称用于，当您编写程序代码更新属性。  名称必须是一个正确的 CLR 字母数字名称，但是，显示名称能包含空格。  
  
 当您设置属性的名称在 DSL 定义时，其显示名称自动设置为名称的副本。  如果编写 Pascal 大小写的名称 \(例如 “FuelGauge”，显示名称将自动包含空格:“汽油表”。  但是，可以显式地设置显示名称为其他值。  
  
 **说明**。  字段的特性的声明在两个位置都显示:  
  
-   在 " 属性 " 窗口底部，当用户选择属性。  您可以将其解释为用户可能该属性表示。  
  
-   在生成的程序代码。  如果使用文档结构提取 API 文档，它将显示为该属性的说明。 API 的。  
  
 **类别**。  类别是在 " 属性 " 窗口的一个标题。  
  
## 显示样式函数  
 某些图形元素动态功能可以表示或 *显示* 为字段的特性。  此类公开的功能由用户更新，并可通过程序代码更加轻松地更新。  
  
 右击 " DSL 定义的形状类，指向 **将显示**，然后选择功能。  
  
 在形状可以显示 **FillColor**、 **OutlineColor**、 **TextColor**、 **OutlineDashStyle**、 **OutlineThickness** 和 **FillGradientMode** 属性。  在连接上可以显示 **颜色**`,`**TextColor**， **DashStyle**和 **粗细** 属性。  在关系图可以显示 **FillColor** 和 **TextColor** 属性。  
  
## 向前:显示相关元素属性  
 在 DSL 的用户在设计时的元素，该元素的属性显示在 " 属性 " 窗口中。  但是，您也可以显示指定的相关元素的属性。  这是有用，如果定义一组元素。  例如，可以定义一个主要组件和一个选项插件元素。  如果主要元素映射到形状，另一个则不是，查看其所有的属性很有用，就好像它们在一个元素。  
  
 这种影响名为 *转发的属性*，并且，它在某些情况下会自动发生。  在某些情况下，您可实现向前通过定义的特性字段类型描述符。  
  
### 向前用例的默认属性  
 当用户选择形状或连接或一个元素在资源管理器时，下面的属性在 " 属性 " 窗口中显示:  
  
-   在模型元素的域类中定义的字段的特性，包括在基类中定义的控件。  异常是将 **可浏览的** 到 `False`的字段的特性。  
  
-   通过关系链接具有重数 0..1 元素的名称。  这会看到选择性地链接元素的一种简便方法，因此，即使未定义连接映射为您的关系。  
  
-   目标元素嵌入关系的字段的特性。  由于嵌入关系没有显式通常显示，这使用户能够看到它们的属性。  
  
-   在选定的形状或连接中定义的字段的特性。  
  
### 添加特性转发  
 若要向前属性，则定义字段类型描述符。  如果有两个字段类之间的域关系，可使用字段类型描述符将质数的字段的属性设置为一个字段的特性的值在第二个域类的。  例如，因此，如果您有书籍域类并创作域类之间的关系，可以使用字段类型描述符进行 name 属性书籍的作者显示在 " 属性 " 窗口中，当用户选择书时。  
  
> [!NOTE]
>  向前只影响属性 " 窗口中的属性，当用户编辑模型。  它不定义在接收类中的一个字段的特性。  如果要访问转发的字段的特性在 DSL 定义的其他部分或在过程代码中，您必须访问转发元素。  
  
 以下过程假定，您将创建一个 DSL。  前几步骤摘要系统必备组件。  
  
##### 向前从另一个组件的属性  
  
1.  创建至少包含两类，在此示例中调用 Book 并创作的一个 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 解决方案。  应具有为的关系类型的书籍中并创作之间。  
  
     源角色 \(角色的重数书籍端\) 应为 0..1 或 1..1，因此，每本书都有一个作者。  
  
2.  在 **DSL 资源管理器**，右击书籍域类，然后单击 **添加新 DomainTypeDescriptor**。  
  
     名为 **自定义属性说明符路径** 的节点显示在 **自定义类型说明符** 节点下。  
  
3.  右击 **自定义类型说明符** 节点，然后单击 **添加新 PropertyPath**。  
  
     新的属性路径显示在 **自定义属性说明符路径** 节点下。  
  
4.  选择新属性路径，并 **属性** 窗口中，设置 **属性中的路径** 为适当的模型元素的路径。  
  
     可以通过单击下箭头编辑树视图的路径此属性右侧的。  有关字段路径的更多信息，请参见 [域路径语法](../modeling/domain-path-syntax.md)。  在编辑时，路径应类似于 **BookReferencesAuthor.Author\/\! 作者**。  
  
5.  设置 **属性** 到作者 **Name** 字段的特性。  
  
6.  设置 **显示名称** 创作名称。  
  
7.  转换所有模板，生成并运行 DSL。  
  
8.  使用引用关系，在模型关系图，创建一个书籍，作者，并将它们。  选择书元素，则本书的属性外，因此，在 " 属性 " 窗口应看到作者名称。  将链接的作者的名称或使用不同的作者链接的书籍，可观察到该书的作者名称更改。  
  
## 自定义属性编辑器  
 " 属性 " 窗口为每个字段属性的类型提供编辑体验的适当默认值。  例如，为枚举的类型，将会看到下拉列表，并且，对于一个数字特性，用户可以输入数值。  这仅适用内置类型。  如果指定外部类型，用户查看属性值，但是，不进行编辑。  
  
 但是，可以指定以下版本和类型:  
  
1.  使用标准类型的其他编辑器。  例如，您可以为字符串特性指定文件路径编辑。  
  
2.  字段的特性的外部类型和它的一个编辑器。  
  
3.  一个 .NET 版本 \(如文件路径编辑也可以创建具有自定义属性编辑器。  
  
     在外部类型和类型之间进行转换，如字符串有一个默认编辑器。  
  
 在 DSL， *外部类型* 不是一个简单的类型的任何类型 \(例如布尔或 Int32\) 或字符串。  
  
#### 定义具有外部类型的字段特性  
  
1.  在 **解决方案资源管理器**，添加一个对包含外部类型的程序集 \(dll\)，在 **Dsl** 项目。  
  
     程序集可以是 .NET 程序集或您提供的程序集。  
  
2.  ，除非这样做，已执行将该类型到 **字段类型** 列表。  
  
    1.  打开 DslDefinition.dsl，然后在 **DSL 资源管理器**，右击根节点，然后单击 **添加新的外部类型**。  
  
         新的项显示在 **字段类型** 节点下。  
  
        > [!WARNING]
        >  菜单项在 DSL 根节点，而不是 **字段类型** 节点。  
  
    2.  设置名称，命名空间新类型 " 属性 " 窗口。  
  
3.  添加字段特性添加到域类以常规方式。  
  
     在 " 属性 " 窗口中，选择该外部类型从下拉列表中 **类型** 字段。  
  
 在此阶段，用户可以查看属性的值，但是，无法编辑它。  显示的值从 `ToString()` 函数获取。  您可以编写设置属性值，如命令或规则的程序代码。  
  
### 设置属性编辑器  
 添加一个 CLR 特性添加到字段的特性，为以下形式:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 通过在 " 属性 " 窗口中，的 **自定义特性** 项可以在属性的属性。  
  
 必须从第二个参数指定的类型派生 `AnEditor` 的类型。  第二个参数应为 <xref:System.Drawing.Design.UITypeEditor> 或 <xref:System.ComponentModel.ComponentEditor>。  有关更多信息，请参见 <xref:System.ComponentModel.EditorAttribute>。  
  
 在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可以指定拥有编辑或所提供的编辑器，如 <xref:System.Windows.Forms.Design.FileNameEditor> 或 <xref:System.Drawing.Design.ImageEditor>。  例如，请使用以下过程具有用户可以输入文件名的属性。  
  
##### 定义文件名字段的特性  
  
1.  添加字段特性添加到 DSL 定义的字段类。  
  
2.  选择新属性。  在 " 属性 " 窗口中 **自定义特性** 字段中，键入以下属性。  若要输入此属性，请单击省略号 **\[...\]** 单独然后输入属性名称和参数:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  将该字段保留属性的类型在其默认设置 **字符串**。  
  
4.  若要测试编辑器中，验证用户可以打开文件名编辑器来编辑字段的特性。  
  
    1.  按 CTRL\+F5 或 F5。  在调试解决方案，请打开测试文件。  创建域类的元素并将其选中。  
  
    2.  在 " 属性 " 窗口中，选择字段的特性。  值字段显示一个省略号 **\[...\]**。  
  
    3.  单击该省略号。  文件将出现对话框。  选择文件并关闭对话框。  文件路径现在是字段的特性的值。  
  
### 定义拥有属性编辑器  
 可以定义拥有编辑。  您了解如何实现向用户可编辑您定义的类型，或编辑一个标准类型以特定方式。  例如，您可以允许用户输入表示公式的字符串。  
  
 通过编写从 <xref:System.Drawing.Design.UITypeEditor>派生类定义的编辑器。  类必须重写:  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>，与用户交互和更新属性值。  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>，指定编辑器是否将打开对话框或提供一个下拉菜单。  
  
 您还可以提供在属性网格将显示属性值的图形化表示形式。  为此，请重写 `GetPaintValueSupported`和 `PaintValue`。  有关更多信息，请参见 <xref:System.Drawing.Design.UITypeEditor>。  
  
> [!NOTE]
>  添加在单独的代码文件的代码隐藏 **Dsl** 项目。  
  
 例如：  
  
```  
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor  
{  
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)  
  {  
    base.InitializeDialog(openFileDialog);  
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";  
    openFileDialog.Title = "Select a text file";  
  }  
}  
  
```  
  
 若要使用此编辑器中，定位到字段的特性的 **自定义特性** :  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 有关更多信息，请参见 <xref:System.Drawing.Design.UITypeEditor>。  
  
## 提供值的下拉列表  
 您可以为用户提供值从列表中选择。  
  
> [!NOTE]
>  此方法提供可在运行时更改的值列表。  如果要提供不更改的列表，请考虑使用枚举类型作为字段的特性的类型。  
  
 若要定义标准值列表，添加到字段的特性具有以下形式的 CLR 特性:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 定义一个从 <xref:System.ComponentModel.TypeConverter> 派生的类。  添加在单独的文件中的代码。 **Dsl** 项目。  例如：  
  
```c#  
/// <summary>  
/// Type converter that provides a list of values   
/// to be displayed in the property grid.  
/// </summary>  
/// <remarks>This type converter returns a list   
/// of the names of all "ExampleElements" in the   
/// current store.</remarks>  
public class MyTypeConverter : System.ComponentModel.TypeConverter  
{  
  /// <summary>  
  /// Return true to indicate that we return a list of values to choose from  
  /// </summary>  
  /// <param name="context"></param>  
  public override bool GetStandardValuesSupported  
    (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Returns true to indicate that the user has   
  /// to select a value from the list  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>If we returned false, the user would   
  /// be able to either select a value from   
  /// the list or type in a value that is not in the list.</returns>  
  public override bool GetStandardValuesExclusive  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Return a list of the values to display in the grid  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>A list of values the user can choose from</returns>  
  public override StandardValuesCollection GetStandardValues  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    // Try to get a store from the current context  
    // "context.Instance"  returns the element(s) that   
    // are currently selected i.e. whose values are being  
    // shown in the property grid.   
    // Note that the user could have selected multiple objects,   
    // in which case context.Instance will be an array.  
    Store store = GetStore(context.Instance);  
  
    List<string> values = new List<string>();  
  
    if (store != null)  
    {  
      values.AddRange(store.ElementDirectory  
        .FindElements<ExampleElement>()  
        .Select<ExampleElement, string>(e =>   
      {  
        return e.Name;  
      }));  
    }  
    return new StandardValuesCollection(values);  
  }  
  
  /// <summary>  
  /// Attempts to get to a store from the currently selected object(s)  
  /// in the property grid.  
  /// </summary>  
  private Store GetStore(object gridSelection)  
  {  
    // We assume that "instance" will either be a single model element, or   
    // an array of model elements (if multiple items are selected).  
  
    ModelElement currentElement = null;  
  
    object[] objects = gridSelection as object[];  
    if (objects != null && objects.Length > 0)  
    {  
      currentElement = objects[0] as ModelElement;  
    }  
    else  
    {  
        currentElement = gridSelection as ModelElement;  
    }  
  
    return (currentElement == null) ? null : currentElement.Store;  
  }  
  
}  
  
```  
  
## 请参阅  
 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)