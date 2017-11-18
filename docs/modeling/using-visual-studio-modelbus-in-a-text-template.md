---
title: "文本模板中使用 Visual Studio ModelBus |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: c496aaa7db6f2260764b413bfdf09f766be87384
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>在文本模板中使用 Visual Studio ModelBus
如果您编写读取模型包含的文本模板[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ModelBus 引用，你可能想要解决访问目标模型的引用。 在这种情况下，你必须调整文本模板以及引用的域特定语言 (Dsl):  
  
-   DSL 都是引用的目标必须有配置为从文本模板访问 ModelBus 适配器。 如果你还可以从其他代码访问 DSL，重新配置的适配器则需要除了标准的 ModelBus 适配器。  
  
     适配器 manager 必须继承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>并且必须具有该属性`[HostSpecific(HostName)]`。  
  
-   模板必须从继承<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。  
  
> [!NOTE]
>  如果你想要读取不包含 ModelBus 引用的 DSL 模型，你可以使用 DSL 项目中生成的指令处理器。 有关详细信息，请参阅[从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)。  
  
 文本模板的详细信息，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>为从文本模板访问创建模型总线适配器  
 若要解决的 ModelBus 引用文本模板中，目标 DSL 必须有兼容的适配器。 文本模板在单独的 AppDomain 中执行[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文档编辑器，并因此适配器必须加载而不是访问 DTE 通过模型。  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>若要创建用于与文本模板兼容的 ModelBus 适配器  
  
1.  如果目标 DSL 解决方案没有**ModelBusAdapter**项目中，创建一个使用 Modelbus 扩展向导：  
  
    1.  下载并安装[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ModelBus 扩展，如果尚未这样做。 有关详细信息，请参阅[可视化和建模 SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
    2.  打开 DSL 定义文件。 右击设计图面，然后单击**启用 Modelbus**。  
  
    3.  在对话框中，选择**我想要公开到 ModelBus 此 DSL**。 如果您希望此 DSL 同时才能公开其模型以及使用对其他 dsl 相关联的引用，你可以选择这两个选项。  
  
    4.  单击“确定”。 新项目“ModelBusAdapter”随即添加到 DSL 解决方案中。  
  
    5.  单击**转换所有模板**。  
  
    6.  重新生成解决方案。  
  
2.  如果你想要访问 DSL，从文本模板和其他代码，如命令，从重复**ModelBusAdapter**项目：  
  
    1.  在 Windows 资源管理器，复制并粘贴包含的文件夹**ModelBusAdapter.csproj**。  
  
    2.  重命名项目文件 (例如，若要**T4ModelBusAdapter.csproj**)。  
  
    3.  在**解决方案资源管理器**，右键单击解决方案节点，指向**添加**，然后单击**现有项目**。 找到新的适配器项目中， **T4ModelBusAdapter.csproj**。  
  
    4.  在每个`*.tt`文件的新项目中，更改命名空间。  
  
    5.  右键单击解决方案资源管理器中的新项目，然后单击属性。 在属性编辑器中，更改生成的程序集和默认命名空间的名称。  
  
    6.  在 DslPackage 项目中，添加对新的适配器项目的引用，以便它具有对这两个适配器的引用。  
  
    7.  在 DslPackage\source.extension.tt，添加一行，其中引用新的适配器项目。  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **转换所有模板**和重新生成解决方案。 没有生成错误应发生。  
  
3.  在新的适配器项目中，添加对以下程序集的引用：  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  在 AdapterManager.tt:  
  
    -   更改 AdapterManagerBase 的声明，以便它继承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   在文件末尾附近替换之前 AdapterManager 类 HostSpecific 特性。 删除以下行：  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         插入以下行：  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         此属性筛选器适配器的搜索 modelbus 使用者时可用的适配器集。  
  
5.  **转换所有模板**和重新生成解决方案。 没有生成错误应发生。  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>编写文本模板可以解析 ModelBus 引用  
 通常情况下，开始读取，并生成文件从"source"DSL 的模板。 此模板使用在源 DSL 项目读取中所述的方式中的源模型文件中生成的指令[从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)。 但是，源 DSL 包含到"目标"DSL ModelBus 引用。 因此想要启用要解析的引用和访问目标 DSL 的模板代码。 因此必须通过执行以下步骤来调整模板：  
  
-   更改到模板的基本类<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。  
  
-   包括`hostspecific="true"`的 template 指令中。  
  
-   将程序集引用添加到目标 DSL 和其适配器，并启用 ModelBus。  
  
-   不需要作为目标 DSL 的一部分生成的指令。  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let's assume they're all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 此文本模板执行时，`SourceDsl`指令可加载该文件`Sample.source`。 模板可访问该模型中，从开始的元素`this.ModelRoot`。 代码可以使用的域类和属性的该 DSL。  
  
 此外，该模板可以解析 ModelBus 引用。 其中的引用是指向目标模型，程序集指令允许使用的域类和属性的该模型的 DSL 的代码。  
  
-   如果不使用由 DSL 项目生成的指令，还应包括以下。  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   使用`this.ModelBus`获得对 ModelBus 访问权限。  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>演练： 测试使用 ModelBus 的文本模板  
 在本演练中，你将执行以下步骤：  
  
1.  构造两个 Dsl。 一个 DSL*使用者*，具有`ModelBusReference`属性，可以参考其他 DSL*提供程序*。  
  
2.  提供程序中创建两个 ModelBus 适配器： 一个用于通过文本模板，另一个用于普通的代码的访问权限。  
  
3.  单个实验项目中创建 Dsl 实例的模型。  
  
4.  在一个模型，以指向其他模型中设置域属性。  
  
5.  编写的双击处理程序将打开指向模型。  
  
6.  编写一个文本模板，可以加载第一个模型，遵循对其他模型，引用并读取其他模型。  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>构造访问 ModelBus DSL  
  
1.  创建一个新的 DSL 解决方案。 对于此示例中，选择任务流解决方案模板。 将语言名称设置为`MBProvider`和到".provide"的文件扩展名。  
  
2.  在 DSL 定义关系图中，右键单击靠近顶部，不是关系图的空白部分，然后单击**启用 Modelbus**。  
  
    -   如果看不到**启用 Modelbus**，你必须下载并安装 VMSDK ModelBus 扩展。 在 VMSDK 站点上找到它：[可视化和建模 SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
3.  在**启用 Modelbus**对话框中，选择**公开到 ModelBus 此 DSL**，然后单击**确定**。  
  
     一个新的项目， `ModelBusAdapter`，添加到解决方案。  
  
 你现在具有可由 ModelBus 通过文本模板访问 DSL。 可以在代码中的命令、 事件处理程序或所有这些模型文件编辑器在 AppDomain 中运行的规则，解析对它的引用。 但是，文本模板在单独的 AppDomain 中运行，并且正在编辑的情况下无法访问的模型。 如果你想要访问 ModelBus 引用到此 DSL 从文本模板，你必须单独 ModelBusAdapter。  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>若要创建用于为文本模板配置的 ModelBus 适配器  
  
1.  在 Windows 资源管理器，复制并粘贴包含 ModelBusAdapter.csproj 的文件夹。  
  
     该文件夹 T4ModelBusAdapter 命名。  
  
     重命名项目文件 T4ModelBusAdapter.csproj。  
  
2.  在解决方案资源管理器，将添加到 MBProvider 解决方案的 T4ModelBusAdapter。 右键单击解决方案节点，指向**添加**，然后单击**现有项目**。  
  
3.  右键单击 T4ModelBusAdapter 项目节点，然后单击属性。 在项目属性窗口中，更改**程序集名称**和**默认 Namespace**到`Company.MBProvider.T4ModelBusAdapters`。  
  
4.  在每个 *.tt 文件中 T4ModelBusAdapter，插入"T4"的最后一个部分的命名空间，以便行如下所示。  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  在`DslPackage`项目中，添加的项目引用`T4ModelBusAdapter`。  
  
6.  在 DslPackage\source.extension.tt，添加以下行下的`<Content>`。  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  在`T4ModelBusAdapter`项目中，添加对的引用： **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  打开 T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  将 AdapterManagerBase 的基类更改为 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。 此文件的一部分，现在如下所示。  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  该文件末尾附近插入前面类 AdapterManager 以下其他属性。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         结果如下所示。  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. 单击**转换所有模板**在标题栏的解决方案资源管理器。  
  
10. 重新生成解决方案。 单击 F5。  
  
11. 验证 DSL 正在通过按 F5。 在实验性的项目中，打开`Sample.provider`。 关闭 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的实验实例。  
  
 在文本模板以及在普通的代码，则现在可以解析对此 DSL 的 ModelBus 引用。  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>构造与 ModelBus 引用域属性 DSL  
  
1.  通过使用最小语言解决方案模板创建新的 DSL。 命名语言 MBConsumer 并设置为".consume"的文件扩展名。  
  
2.  在 DSL 项目中，添加 MBProvider DSL 的程序集的引用。 右键单击`MBConsumer\Dsl\References`，然后单击**添加引用**。 在**浏览**选项卡上，找到`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     这使你可以创建使用其他 DSL 的代码。 如果你想要创建对多个 Dsl 的引用，则还添加它们。  
  
3.  在 DSL 定义关系图中，右击关系图，然后单击**启用 ModelBus**。 在对话框中，选择**启用此 DSL 使用 ModelBus**。  
  
4.  在类中`ExampleElement`，添加一个新的域属性`MBR`，并在属性窗口中，将其类型设置为`ModelBusReference`。  
  
5.  右键单击关系图上的 domain 属性，然后单击**编辑 ModelBusReference 特定属性**。 在对话框中，选择**将模型元素**。  
  
     设置为以下文件对话框筛选器。  
  
     `Provider File|*.provide`  
  
     后的子字符串"&#124;"为文件选择对话框中的筛选器。 你无法将其设置为允许通过将任何文件 *。\*  
  
     在**模型元素类型**列表中，在提供程序 DSL (例如，Company.MBProvider.Task) 中输入的一个或多个域类的名称。 它们可以是抽象类。 如果列表为空，则用户可以设置对任何元素的引用。  
  
6.  关闭对话框并**转换所有模板**。  
  
 您已创建 DSL 都可以包含对另一个 DSL 中的元素的引用。  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>在解决方案中创建到另一个文件 ModelBus 引用  
  
1.  在 MBConsumer 解决方案中，按 CTRL + F5。 实验实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在中打开**MBConsumer\Debugging**项目。  
  
2.  添加一份到 Sample.provide **MBConsumer\Debugging**项目。 这是必需的因为 ModelBus 引用必须引用同一解决方案中的文件。  
  
    1.  右键单击调试项目，指向**添加**，然后单击**现有项**。  
  
    2.  在**添加项**对话框中，将筛选器设置**所有文件 (\*。\*)**.  
  
    3.  导航到`MBProvider\Debugging\Sample.provide`，然后单击**添加**。  
  
3.  打开 `Sample.consume`。  
  
4.  单击一个示例形状，然后在属性窗口中，单击**[…]** MBR 属性中。 在对话框中，单击**浏览**和选择`Sample.provide`。 在元素窗口中，展开类型任务并选择其中一个元素。  
  
5.  保存该文件。  
  
     (不要关闭的实验实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。)  
  
 您已创建包含到另一个模型中的元素的 ModelBus 引用的模型。  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>解析文本模板中的 ModelBus 引用  
  
1.  在实验实例中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，打开示例文本模板文件。 将其内容设置，如下所示。  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     请注意以下内容：  
  
    1.  `hostSpecific`和`inherits`属性`template`指令必须设置。  
  
    2.  通过在该 DSL 生成指令处理器的常用方式访问的使用者模型。  
  
    3.  程序集和导入指令必须能够访问 ModelBus 和提供程序 DSL 的类型。  
  
    4.  如果你知道，许多 Mbr 会链接到相同的模型，它是更好的做法调用 CreateAdapter 仅一次。  
  
2.  保存模板。 验证生成的文本文件如下所示。  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>解决笔势处理程序中的 ModelBus 引用  
  
1.  关闭实验实例的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，如果它正在运行。  
  
2.  添加名为 MBConsumer\Dsl\Custom.cs 并将其内容设置为以下文件。  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  按 Ctrl+F5。  
  
4.  在实验实例中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，打开`Debugging\Sample.consume`。  
  
5.  双击一个形状。  
  
     如果该元素上设置 MBR，被引用的模型将打开，并且引用的元素处于选中状态。  
  
## <a name="see-also"></a>另请参阅  
 [通过使用 Visual Studio Modelbus 集成模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
