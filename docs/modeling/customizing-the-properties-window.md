---
title: "自定义属性窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, Properties window
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: "20"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 962b4a8eac0d548d2c7a337207644bdc717fe3cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-the-properties-window"></a>自定义“属性”窗口
你可以自定义的外观和行为的属性窗口中你的域特定语言 (DSL) 中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在 DSL 定义中，每个域类上定义域属性。 默认情况下时选择的类，在图上或在模型资源管理器的实例, 的每个域属性将列在属性窗口中。 这样你可以查看和编辑域属性值，即使你具有不到关系图上的形状字段映射它们。  
  
## <a name="names-descriptions-and-categories"></a>名称、 说明和类别  
 **名称和显示名称**。 在域属性的定义中，属性显示名称是在运行时在属性窗口中显示的名称。 与此相反，当你编写的程序代码以更新属性，使用的名称。 名称必须是正确的 CLR 字母数字名称中，但显示名称可以包含空格。  
  
 DSL 定义中设置属性的名称时，其显示名称是自动设置为该名称的副本。 如果您编写一个 Pascal 壳的名称，例如"FuelGauge"，显示名称将自动包含空格:"燃料仪表"。 但是，可以为其他值显式设置显示名称。  
  
 **说明**。 域属性的说明将显示在两个位置：  
  
-   在底部的属性窗口时用户选择的属性。 可用于向用户解释该属性表示。  
  
-   在生成的程序代码中。 如果你使用的文档功能来提取 API 文档，它将显示为 API 中的此属性的说明。  
  
 **Category**。 类别是属性窗口中的标题。  
  
## <a name="exposing-style-features"></a>公开样式功能  
 您可以表示某些图形元素的动态功能或*公开*作为域属性。 可以由用户更新已以这种方式公开的功能，可以更多轻松地更新、 程序代码。  
  
 右键单击 DSL 定义中的形状类，指向**添加公开**，然后选择一项功能。  
  
 在形状上可以公开**FillColor**， **OutlineColor**， **TextColor**， **OutlineDashStyle**， **OutlineThickness**和**FillGradientMode**属性。 您可以公开的连接器**颜色**`,`**TextColor**， **DashStyle**，和**粗细**属性。 在关系图上可以公开**FillColor**和**TextColor**属性。  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>转发： 显示的相关元素的属性  
 DSL 的用户在模型中选择一个元素，该元素的属性将显示在属性窗口中。 但是，你还可以显示的指定相关的元素的属性。 这很有用，如果已定义一起工作的一组元素。 例如，你可以定义主要元素和可选的插件元素。 如果的主要元素映射到一个形状，另一个不是很有用，若要查看其所有属性，就像它们是上一个元素。  
  
 名为这种效果*属性转发*，并在某些情况下自动发生。 在其他情况下，你可以实现转发通过定义的域类型描述符的属性。  
  
### <a name="default-property-forwarding-cases"></a>默认属性转发用例  
 当用户在资源管理器中选择一种形状或连接器或元素时，在属性窗口中显示以下属性：  
  
-   模型元素，包括那些在基类中定义的域类定义的域属性。 例外情况是域属性已设置**是可浏览**到`False`。  
  
-   通过具有多重性的 0..1 关系链接的元素的名称。 这提供 （可选） 查看的简便方法链接元素，即使你未定义关系的连接器映射。  
  
-   嵌入的元素为目标的关系的域属性。 通常不显式显示嵌入的关系，因为这会使用户可以查看其属性。  
  
-   在所选的形状或连接器定义的域属性。  
  
### <a name="adding-property-forwarding"></a>添加属性转发  
 若要将转发属性，你定义的域类型描述符。 如果你有两个域类之间的域关系，可以使用的域类型说明符在第二个域类中的域属性的值的第一个类中设置域属性。 例如，如果你有之间的关系**簿**域类和**作者**域类，你可以使用的域类型描述符以便**名称**属性本书的**作者**出现在属性窗口中，当用户选择书籍。  
  
> [!NOTE]
>  如果用户正在编辑的模型，属性转发会影响仅属性窗口。 它不接收类上定义的域属性。 如果你想要访问的转发的 domain 属性中 DSL 定义的其他部分或在程序代码中，你必须访问转发元素。  
  
 以下过程假定你已创建 DSL。 第一个的几个步骤总结了系统必备组件。  
  
##### <a name="to-forward-a-property-from-another-element"></a>若要从另一个元素转发属性  
  
1.  创建[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]包含至少两个类，它在此示例中称为解决方案**簿**和**作者**。 应该有任意一种类型之间的关系**簿**和**作者**。  
  
     源 role 多重性 (中的角色**簿**端) 应为 0..1 或 1..1，因此每个**簿**有一个**作者**。  
  
2.  在**DSL 资源管理器**，右键单击**簿**域类，然后单击**添加新 DomainTypeDescriptor**。  
  
     名为的节点**自定义属性描述符的路径**下显示**自定义类型描述符**节点。  
  
3.  右键单击**自定义类型描述符**节点，，然后单击**添加新 PropertyPath**。  
  
     新的属性路径显示在**自定义属性描述符的路径**节点。  
  
4.  选择新的属性路径，然后在**属性**窗口中，设置**属性路径**为相应的模型元素的路径。  
  
     通过单击该属性右侧的向下箭头，可以编辑在树视图中的路径。 有关域路径的详细信息，请参阅[域路径语法](../modeling/domain-path-syntax.md)。 如果你编辑了它，路径应类似于**BookReferencesAuthor.Author/ ！作者**。  
  
5.  设置**属性**到**名称**域属性**作者**。  
  
6.  设置**显示名称**到**创作名称**。  
  
7.  转换所有模板、 生成和运行 DSL。  
  
8.  在模型图中，创建一本书中，作者，并将这些链接使用引用关系。 选择该书籍元素，并在属性窗口中，您应看到作者姓名除了书籍的属性。 更改名称的链接的作者，或将书链接到不同的作者，并观察书作者姓名更改。  
  
## <a name="custom-property-editors"></a>自定义属性编辑器  
 属性窗口中提供相应的默认值编辑为每个域属性的类型的体验。 例如，对于枚举类型，则用户将看到的下拉列表，并对于数值属性，用户可以输入数字。 这是仅适用于内置类型。 如果指定外部类型时，用户将能够查看该属性的值，但不是能编辑它。  
  
 但是，你可以指定以下编辑器和类型：  
  
1.  通过标准的类型使用的另一个编辑器。 例如，你可以指定为字符串属性的文件路径编辑器。  
  
2.  域属性，以及为其编辑器为外部类型。  
  
3.  如文件路径编辑器中，或你的.NET 编辑器可以创建你自己的自定义属性编辑器。  
  
     为外部类型和字符串，具有一个默认编辑器，例如类型之间转换。  
  
 在 DSL*外部类型*是不是一个简单类型 （如布尔值或 Int32） 或字符串的任何类型。  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>若要定义域属性具有的外部类型  
  
1.  在**解决方案资源管理器**，添加对程序集 (DLL) 中包含的外部类型的引用**Dsl**项目。  
  
     程序集可以是.NET 程序集或您提供的程序集。  
  
2.  添加到类型**域类型**列表，除非你已这样做。  
  
    1.  打开 DslDefinition.dsl，然后在**DSL 资源管理器**，右键单击根节点，然后单击**添加新的外部类型**。  
  
         在下，将出现一个新项**域类型**节点。  
  
        > [!WARNING]
        >  菜单项的 DSL 根节点上，不是**域类型**节点。  
  
    2.  在属性窗口中设置的名称和新类型的命名空间。  
  
3.  将域属性添加到域类中，按常规方式。  
  
     在属性窗口中，从下拉列表中选择外部类型**类型**字段。  
  
 在此阶段，用户可以查看的属性的值，但它们不能编辑它。 显示的值从获得`ToString()`函数。 你可以编写在命令行或规则例如设置的属性的值的程序代码。  
  
### <a name="setting-a-property-editor"></a>设置属性编辑器  
 将 CLR 特性添加到域属性，采用以下形式：  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 你可以在属性上设置该属性，通过使用**自定义特性**属性窗口中的条目。  
  
 一种`AnEditor`必须从第二个参数中指定的类型派生。 第二个参数应为<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.ComponentEditor>。 有关更多信息，请参见<xref:System.ComponentModel.EditorAttribute>。  
  
 你可以指定您自己的编辑器或编辑器中提供[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，如<xref:System.Windows.Forms.Design.FileNameEditor>或<xref:System.Drawing.Design.ImageEditor>。 例如，使用以下过程为具有用户可以在其中输入文件名称属性。  
  
##### <a name="to-define-a-file-name-domain-property"></a>若要定义的文件名称域属性  
  
1.  将域属性添加到你的 DSL 定义中的域类。  
  
2.  选择新的属性。 在**自定义特性**字段在属性窗口中，输入以下属性。 若要输入此属性，单击省略号**[…]**然后单独输入属性名称和参数：  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  将保留其默认设置域属性的类型**字符串**。  
  
4.  若要测试编辑器，请验证用户可以打开文件名称编辑器，若要编辑域属性。  
  
    1.  按 CTRL + F5。 在调试的解决方案中，打开一个测试文件。 创建的域类元素，然后选择它。  
  
    2.  在属性窗口中，选择域属性。 值字段显示省略号**[…]**.  
  
    3.  单击省略号。 出现文件对话框。 选择文件并关闭对话框。 文件路径现域属性的值。  
  
### <a name="defining-your-own-property-editor"></a>定义你自己的属性编辑器  
 你可以定义自己的编辑器。 你执行此操作以允许用户编辑已定义的类型或者以特殊方式编辑标准的类型。 例如，你可以允许用户输入表示公式的字符串。  
  
 通过编写的类派生自定义编辑器<xref:System.Drawing.Design.UITypeEditor>。 你的类必须重写：  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>与用户交互，并更新属性值。  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>指定你的编辑器是否将会打开一个对话框或提供一个下拉列表菜单。  
  
 你还可以提供的图形表示形式将显示在属性网格中的属性的值。 若要执行此操作，重写`GetPaintValueSupported`，和`PaintValue`。  有关更多信息，请参见<xref:System.Drawing.Design.UITypeEditor>。  
  
> [!NOTE]
>  在单独的代码文件中添加代码**Dsl**项目。  
  
 例如:   
  
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
  
 若要使用此编辑器，设置**自定义特性**的某一域属性：  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 有关更多信息，请参见<xref:System.Drawing.Design.UITypeEditor>。  
  
## <a name="providing-a-drop-down-list-of-values"></a>提供值的下拉的列表  
 你可以提供的用户可供选择值的列表。  
  
> [!NOTE]
>  此方法提供可以在运行时更改的值的列表。 如果你想要提供不会更改的列表，请考虑改为使用的枚举的类型作为域属性的类型。  
  
 若要定义的标准值列表，你将添加到你域的属性具有以下形式的 CLR 属性：  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 定义一个从 <xref:System.ComponentModel.TypeConverter> 派生的类。 在单独的文件中添加代码**Dsl**项目。 例如:   
  
```csharp  
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
  
## <a name="see-also"></a>另请参阅  
 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)