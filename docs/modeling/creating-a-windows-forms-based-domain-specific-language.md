---
title: "创建 Windows 窗体的基于域特定语言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 17
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c9caf1da3e6e9d065a94e6b12b7699cd5a381ea2
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>创建基于 Windows 窗体的域特定语言
Windows 窗体可用于显示特定于域的语言 (DSL) 模型，而不是使用 DSL 关系图的状态。 本主题将指导您完成将 Windows 窗体绑定到 DSL，请使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可视化和建模 SDK。  
  
 ![DSL-Wpf-2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
DSL 实例中，显示 Windows 窗体用户界面和模型资源管理器。  
  
## <a name="creating-a-windows-forms-dsl"></a>创建 Windows 窗体 DSL  
 **最小 WinForm 设计器**DSL 模板将创建可以进行修改以满足您自己的要求的最小 DSL。  
  
#### <a name="to-create-a-minimal-winforms-dsl"></a>若要创建的最小的 WinForms DSL  
  
1.  创建从 DSL**最小 WinForm 设计器**模板。  
  
     在本演练中，假定以下名称︰  
  
    |||  
    |-|-|  
    |解决方案和 DSL 名称|FarmApp|  
    |Namespace|Company.FarmApp|  
  
2.  该模板提供的初始示例试验︰  
  
    1.  转换所有模板。  
  
    2.  生成并运行该示例 (**CTRL + F5**)。  
  
    3.  在 Visual Studio 的实验实例中，打开`Sample`调试的项目中的文件。  
  
         请注意显示 Windows 窗体控件。  
  
         此外可以查看模型浏览器中显示的元素。  
  
         添加一些元素在窗体或资源管理器，并注意到它们出现在其他显示器。  
  
 中的主实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，注意到 DSL 解决方案有关的以下几点︰  
  
-   `DslDefinition.dsl`不包含任何关系图元素。 这是因为未将使用 DSL 关系图以查看此 DSL 的实例模型。 相反，会将 Windows 窗体绑定到模型中，并在窗体上的元素将显示该模型。  
  
-   除了`Dsl`和`DslPackage`项目中，该解决方案包含一个名为的第三个项目`UI.` **UI**项目包含一个 Windows 窗体控件的定义。 `DslPackage`取决于`UI`，和`UI`取决于`Dsl`。  
  
-   在`DslPackage`项目中，`UI\DocView.cs`包含显示在中定义的 Windows 窗体控件的代码`UI`项目。  
  
-   `UI`项目包含窗体控件绑定到 DSL 的工作示例。 但是，它不起作用时您已更改 DSL 定义中。 `UI`项目包含︰  
  
    -   一个名为 Windows 窗体类`ModelViewControl`。  
  
    -   名为的文件`DataBinding.cs`，它包含的其他部分定义`ModelViewControl`。 若要查看其内容在**解决方案资源管理器**，打开该文件的快捷菜单并选择**查看代码**。  
  
### <a name="about-the-ui-project"></a>有关用户界面项目  
 更新要定义您自己的 DSL 的 DSL 定义文件时，您将需要更新中的控件`UI`项目以显示你的 DSL。 与不同`Dsl`和`DslPackage`项目，该示例`UI`项目没有从生成`DslDefinitionl.dsl`。 您可以添加.tt 文件生成的代码，如果您希望，尽管这不包括在本演练中。  
  
## <a name="updating-the-dsl-definition"></a>更新 DSL 定义  
 本演练中使用 DSL 定义下面。  
  
 ![DSL Wpf&1;](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  
  
#### <a name="to-update-the-dsl-definition"></a>若要更新 DSL 定义  
  
1.  在 DSL 设计器中打开 DslDefinition.dsl。  
  
2.  删除**ExampleElement**  
  
3.  重命名**ExampleModel**域类传递给`Farm`。  
  
     为它提供了其他域属性名为`Size`类型的**Int32**，和`IsOrganic`类型的**布尔**。  
  
    > [!NOTE]
    >  如果您删除根域类，然后创建一个新的根目录，您将必须重置的编辑器根类属性。 在**DSL 资源管理器**，选择**编辑器**。 然后在属性窗口中设置**根类**到`Farm`。  
  
4.  使用**已命名域类**工具来创建以下域类︰  
  
    -   `Field`– 为此提供一个名为其他域属性`Size`。  
  
    -   `Animal`– 在属性窗口中，设置**继承修饰符**到**抽象**。  
  
5.  使用**域类**工具来创建以下类︰  
  
    -   `Sheep`  
  
    -   `Goat`  
  
6.  使用**继承**工具以进行`Goat`和`Sheep`继承`Animal`。  
  
7.  使用**Embedding**工具嵌入`Field`和`Animal`下`Farm`。  
  
8.  您可能想要整理关系图。 若要减少重复的元素的数量，请使用**将子树放在此处**叶元素的快捷菜单命令。  
  
9. **转换所有模板**在解决方案资源管理器的工具栏中。  
  
10. 生成**Dsl**项目。  
  
    > [!NOTE]
    >  在此阶段，其他项目将不生成，没有错误。 但是，我们想要生成的 Dsl 项目，以便它的程序集可供数据源向导。  
  
## <a name="updating-the-ui-project"></a>更新用户界面项目  
 现在可以创建新的用户控件将显示存储在 DSL 模型的信息。 若要连接到模型的用户控件的最简单方法是通过数据绑定。 数据绑定适配器类型名为**ModelingBindingSource**专门用来连接到非 VMSDK 接口的 Dsl。  
  
#### <a name="to-define-your-dsl-model-as-a-data-source"></a>若要将 DSL 模型定义为数据源  
  
1.  在**数据**菜单上，选择**显示数据源**。  
  
     **数据源**窗口随即打开。  
  
     选择**添加新数据源**。 **数据源配置向导**随即打开。  
  
2.  选择**对象**，**下一步**。  
  
     展开**Dsl**， **Company.FarmApp**，然后选择**场**，这是您的模型的根类。 选择**完成**。  
  
     在解决方案资源管理器， **UI**项目现在包含**Properties\DataSources\Farm.datasource**  
  
     属性和关系的 model 类显示在数据源窗口。  
  
     ![DslWpf&3;](../modeling/media/dslwpf-3.png "DslWpf&3;")  
  
#### <a name="to-connect-your-model-to-a-form"></a>若要将您的模型连接到窗体  
  
1.  在**UI**项目中，删除所有现有的.cs 文件。  
  
2.  添加一个新**用户控件**名为文件`FarmControl`到**UI**项目。  
  
3.  在**数据源**窗口上的下拉列表菜单**场**，选择**详细信息**。  
  
     保留其他属性的默认设置。  
  
4.  在设计视图中打开 FarmControl.cs。  
  
     拖动**场**从 FarmControl 到数据源窗口。  
  
     控件将显示一组，一个用于每个属性。 关系属性不会生成控件。  
  
5.  删除**farmBindingNavigator**。 这也会自动生成中`FarmControl`设计器中，但这不是为此应用程序很有用。  
  
6.  使用工具箱中，创建两个实例**DataGridView**，并将它们`AnimalGridView`和`FieldGridView`。  
  
    > [!NOTE]
    >  一个可选步骤是将数据源窗口拖到控件中拖放动物和字段项目。 此操作会自动创建数据网格和网格视图和数据源之间的绑定。 但是，此绑定无法正常工作的 Dsl。 因此最好创建数据网格和绑定手动。  
  
7.  如果工具箱中不包含**ModelingBindingSource**工具时，将其添加。 在快捷菜单上的**数据**选项卡上，选择**选择项**。 在**选择工具箱项**对话框中，选择**ModelingBindingSource**从**.NET Framework 选项卡上**。  
  
8.  使用工具箱中，创建两个实例**ModelingBindingSource**，并将它们`AnimalBinding`和`FieldBinding`。  
  
9. 设置**DataSource**每个属性**ModelingBindingSource**到**farmBindingSource**。  
  
     设置**DataMember**属性设置为**动物**或**字段**。  
  
10. 设置**DataSource**属性`AnimalGridView`到`AnimalBinding`，和`FieldGridView`到`FieldBinding`。  
  
11. 调整您的味道该场控件的布局。  
  
 **ModelingBindingSource**执行特定于 Dsl 的多个功能是适配器︰  
  
-   它在 VMSDK 存储事务中包装更新。  
  
     例如，当用户从数据视图网格中删除某一行，正则绑定将导致事务异常。  
  
-   它可以确保，当用户选择的行，则属性窗口将显示相应的模型元素，而不是数据网格行的属性。  
  
 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
数据源和视图之间的链接的架构。  
  
#### <a name="to-complete-the-bindings-to-the-dsl"></a>若要完成到 DSL 的绑定  
  
1.  在单独的代码文件中添加以下代码**UI**项目︰  
  
    ```c#  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace Company.FarmApp  
    {  
      partial class FarmControl  
      {  
        public IContainer Components { get { return components; } }  
  
        /// <summary>Binds the WinForms data source to the DSL model.  
        /// </summary>  
        /// <param name="nodelRoot">The root element of the model.</param>  
        public void DataBind(ModelElement modelRoot)  
        {  
          WinFormsDataBindingHelper.PreInitializeDataSources(this);  
          this.farmBindingSource.DataSource = modelRoot;  
          WinFormsDataBindingHelper.InitializeDataSources(this);  
        }  
      }  
    }  
    ```  
  
2.  在**DslPackage**项目中，编辑**DslPackage\DocView.tt**更新以下变量定义︰  
  
    ```c#  
    string viewControlTypeName = "FarmControl";  
    ```  
  
## <a name="testing-the-dsl"></a>测试 DSL  
 DSL 解决方案现在可以生成并运行，尽管您可能想要添加更多改进更高版本。  
  
#### <a name="to-test-the-dsl"></a>若要测试 DSL  
  
1.  生成和运行解决方案。  
  
2.  在 Visual Studio 的实验实例中，打开**示例**文件。  
  
3.  在**FarmApp 资源管理器**，打开快捷菜单上**场**根节点，然后选择**添加新 Goat**。  
  
     `Goat1`将出现在**动物**视图。  
  
    > [!WARNING]
    >  您必须使用的快捷菜单上**场**节点中，不**动物**节点。  
  
4.  选择**场**根节点并查看其属性。  
  
     在窗体视图中，更改**名称**或**大小**的场。  
  
     当你离开在表单中，在属性窗口中的相应属性更改的每个字段。  
  
## <a name="enhancing-the-dsl"></a>增强 DSL  
  
#### <a name="to-make-the-properties-update-immediately"></a>要让立即更新的属性  
  
1.  在 FarmControl.cs 设计视图中，选择一个简单的字段，例如名称、 大小或 IsOrganic。  
  
2.  在属性窗口中，展开**DataBindings**并打开**（高级）**。  
  
     在**格式设置和高级绑定**对话框下**数据源更新模式**，选择**OnPropertyChanged**。  
  
3.  生成和运行解决方案。  
  
     当您更改场的模型更改立即的相应属性字段的内容时，请验证的。  
  
#### <a name="to-provide-add-buttons"></a>提供添加按钮  
  
1.  在 FarmControl.cs 设计视图中，使用工具箱窗体上创建的按钮。  
  
     编辑在名称和文本按钮，例如到`New Sheep`。  
  
2.  在按钮背后的代码 （例如双击以打开它）。  
  
     其进行编辑，如下所示︰  
  
    ```c#  
    private void NewSheepButton_Click(object sender, EventArgs e)  
    {  
      using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
      {  
        elementOperations.MergeElementGroup(farm,  
          new ElementGroup(new Sheep(farm.Partition)));  
        t.Commit();  
      }  
    }  
  
    // The following code is shared with other add buttons:  
    private ElementOperations operationsCache = null;  
    private ElementOperations elementOperations  
    {  
      get  
      {  
        if (operationsCache == null)  
        {  
          operationsCache = new ElementOperations(farm.Store, farm.Partition);  
        }  
        return operationsCache;  
      }  
    }  
    private Farm farm  
    {  
      get { return this.farmBindingSource.DataSource as Farm; }  
    }  
  
    ```  
  
     您还需要插入以下指令︰  
  
    ```c#  
  
    using Microsoft.VisualStudio.Modeling;  
  
    ```  
  
3.  添加类似按钮 Goats 和字段。  
  
4.  生成和运行解决方案。  
  
5.  验证新建按钮添加一项。 FarmApp 浏览器中，在适当的数据网格视图中，应显示新项。  
  
     您应能够编辑数据网格视图中的元素的名称。 此外可以在从那里删除它。  
  
 ![DSL Wpf&2;](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
  
### <a name="about-the-code-to-add-an-element"></a>有关用于添加一个元素的代码  
 对于新的元素按钮，以下替代代码是稍微简单些。  
  
```c#  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  
  
```  
  
 但是，此代码不设置新项的默认名称。 不会运行任何您可能已定义中的自定义的合并**元素合并指令**的 DSL，并且不执行任何可能已定义的自定义合并代码。  
  
 因此我们建议你使用<xref:Microsoft.VisualStudio.Modeling.ElementOperations>来创建新元素。</xref:Microsoft.VisualStudio.Modeling.ElementOperations> 有关详细信息，请参阅[自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何定义特定于域的语言](../modeling/how-to-define-a-domain-specific-language.md)   
 [编写代码以自域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Visual Studio 的建模 SDK - 特定于域的语言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
