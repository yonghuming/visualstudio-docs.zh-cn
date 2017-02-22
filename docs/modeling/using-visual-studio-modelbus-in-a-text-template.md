---
title: "在文本模板中使用 Visual Studio ModelBus | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 在文本模板中使用 Visual Studio ModelBus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果编写读取的文本模板中包含的设计 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 引用，则可能要解析对访问目标架构。  在这种情况下，必须满足文本模板和引用的域特定语言 \(DSLs\):  
  
-   DSL 是目标的引用必须为从文本模板访问配置的 ModelBus 适配器。  除了标准 ModelBus 适配器外，如果您还可以从访问其他代码的 DSL，重新配置的适配器需要。  
  
     适配器经理必须从 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> 继承，且必须具有属性 `[HostSpecific(HostName)]`。  
  
-   模板必须从 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>继承。  
  
> [!NOTE]
>  如果要读取不包含的 DSL 模型 ModelBus 引用，可以在 DSL 项目生成的指令处理器。  有关更多信息，请参见 [从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)。  
  
 有关文本模板的更多信息，请参见[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
## 创建访问受模型总线适配器从文本模板  
 若要解决 ModelBus 引用在文本模板中，目标 DSL 必须具有兼容的适配器。  文本模板在从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的单独的 AppDomain 执行文档编辑器，并适配器必须加载该模型而非访问它通过预置。  
  
#### 创建与文本模板兼容的 ModelBus 适配器  
  
1.  如果目标 DSL 解决方案没有一个 **ModelBusAdapter** 项目，使用 Modelbus 扩展向导，请创建一:  
  
    1.  ，如果尚未执行此操作，请下载并安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 扩展。  有关更多信息，请参见 [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
    2.  打开 DSL 定义文件。  右击该设计图面然后单击 **启用 Modelbus**。  
  
    3.  在对话框中，选择 **我希望显示此 DSL 在 ModelBus**。  可以选择两个选项，如果希望此 DSL 显示其设计，并使用对其他 DSL。  
  
    4.  单击**“确定”**。  一个新项 “ModelBusAdapter”添加到 DSL 解决方案。  
  
    5.  单击 **转换所有模板**。  
  
    6.  重新生成解决方案。  
  
2.  如果要访问 DSL 从文本模板和其他代码，例如命令，请重复 **ModelBusAdapter** 项目:  
  
    1.  在 Windows 资源管理器中，复制和粘贴包含 **ModelBusAdapter.csproj**的文件夹。  
  
    2.  给项目文件重命名为 \(例如，若要 **T4ModelBusAdapter.csproj**\)。  
  
    3.  在 **解决方案资源管理器**，右击解决方案节点，指向 **添加**，然后单击 **现有项目**。  找到新适配器项目， **T4ModelBusAdapter.csproj**。  
  
    4.  在新项目中每 `*.tt` 文件，请更改命名空间。  
  
    5.  右击 " 解决方案资源管理器的新项并单击属性。  在属性编辑器，请更改生成的程序集和默认命名空间的名称。  
  
    6.  在 DslPackage 项目中，添加对新适配器项目，使其具有对两个适配器。  
  
    7.  在 DslPackage \\ source.extension.tt，添加对新适配器项的一行。  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **转换所有模板** 和重新生成解决方案。  编译错误不应发生。  
  
3.  在新适配器项目中，添加对以下程序集的引用:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  在 AdapterManager.tt:  
  
    -   更改 AdapterManagerBase 的声明，以便它从 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>继承。  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   在文件末尾附近的，请替换 HostSpecific 特性在 AdapterManager 该类之前。  移除以下行:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         插入下面的行:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         此属性筛选可用适配器集，当 modelbus 使用者搜索适配器时。  
  
5.  **转换所有模板** 和重新生成解决方案。  编译错误不应发生。  
  
## 编写能解析 ModelBus 的文本模板引用  
 通常，可以读取并生成从 “源” DSL 的文件的模板开始。  此模板在源 DSL 项目生成读取源模型文件提供一种在 [从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)中描述的指令。  但是，源 DSL 包含 ModelBus 对 “目标” DSL。  因此要使模板代码引用解析和访问目标 DSL。  因此必须执行以下步骤来满足模板:  
  
-   更改模板的基类。 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。  
  
-   包括 `hostspecific="true"` 在模板指令。  
  
-   添加程序集引用到目标 DSL 及其适配器和启用 ModelBus。  
  
-   您不需要作为目标 DSL 的一部分，生成的指令。  
  
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
    // (Let’s assume they’re all in the same model file):  
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
  
 当此文本模板时， `SourceDsl` 指令加载文件 `Sample.source`。  模板从 `this.ModelRoot`启动可以访问该模型的元素，。  代码可以使用该 DSL 域类和属性。  
  
 另外，模板可能的解决 ModelBus 引用。  如果引用指向目标架构，程序集指令允许字段类别和该模型的 DSL 属性的代码使用。  
  
-   如果不使用由 DSL 项目生成的指令，还应包括以下内容。  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   使用 `this.ModelBus` 访问 ModelBus 的访问。  
  
## 演练:测试使用 ModelBus 的文本模板  
 在本演练中，请执行以下步骤:  
  
1.  构造两个 DSL。  一个 DSL， *使用者*，可以引用另一个 DSL 的一个 `ModelBusReference` 属性，提供程序。  
  
2.  创建两个 ModelBus 适配器在提供程序:一个从文本模板访问，其他泛型的代码。  
  
3.  创建 DSL 的实例模型在一个测试项目。  
  
4.  将一个模型中的某个字段的特性指向另一个模型。  
  
5.  编写打开模型点的双击处理程序。  
  
6.  编写可加载第一个模型，按照对另一个模型和读取另一个模型的文本模板。  
  
#### 构造到 ModelBus 是可访问的 DSL  
  
1.  创建新的 DSL 解决方案。  对于此示例，选择任务流解决方案模板。  设置语言名称。 `MBProvider` 和文件扩展名设置为 “.provide”。  
  
2.  在 DSL 定义关系图，右击不位于顶部附近关系图的空白部分，然后单击 **启用 Modelbus**。  
  
    -   如果看不到 **启用 Modelbus**，您必须下载和安装 VMSDK ModelBus 扩展。  查找它在 VMSDK 站点: [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  在 **启用 Modelbus** 对话框中，选择 " **显示此 DSL 在 ModelBus**，然后单击 **好**。  
  
     新项目， `ModelBusAdapter`，即添加到解决方案。  
  
 您现在可以从文本模板访问通过 ModelBus 的一个 DSL。  在命令、事件处理程序或规则代码对它可以解析，在模型文件编辑的 AppDomain 中运行。  但是，在中，在编辑时，在单独的 AppDomain 中运行的文本模板和不可访问模型。  如果要访问 ModelBus 对从文本模板，则此 DSL 必须具有单独 ModelBusAdapter。  
  
#### 创建为文本模板配置的 ModelBus 适配器  
  
1.  在 Windows 资源管理器中，复制和粘贴包含 ModelBusAdapter.csproj 的文件夹。  
  
     将文件夹命名为 T4ModelBusAdapter。  
  
     向项目文件 T4ModelBusAdapter.csproj 重命名。  
  
2.  在解决方案资源管理器中，添加 T4ModelBusAdapter 到 MBProvider 解决方案。  右击解决方案节点，指向 **添加**，然后单击 **现有项目**。  
  
3.  右击 T4ModelBusAdapter 项目节点然后单击属性。  在项目属性 " 窗口中，将 **程序集名称** 和 **默认命名空间** 到 `Company.MBProvider.T4ModelBusAdapters`。  
  
4.  在 T4ModelBusAdapter 的每 \*.tt 文件，请插入 “T4”到命名空间中的最后一部分，因此，行类似于以下内容。  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  在 `DslPackage` 项目中，添加对项目的项目引用。 `T4ModelBusAdapter`。  
  
6.  在 DslPackage \\ source.extension.tt，添加下面的行。 `<Content>`下。  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  在 `T4ModelBusAdapter` 项目中，添加对: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  打开 T4ModelBusAdapter \\AdapterManager .tt:  
  
    1.  更改 AdapterManagerBase 基类。 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。  此文件的部分现在类似于以下内容。  
  
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
  
    2.  在文件末尾附近的，在类 AdapterManager 前面的以下附加属性。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         则结果将类似于以下内容。  
  
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
  
9. 单击 **转换所有模板** 在标题栏解决方案资源管理器中。  
  
10. 重新生成解决方案。  单击 F5。  
  
11. 验证 DSL 工作项按 F5 旁边。  在实验项目中，打开 `Sample.provider`。  关闭 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的实验实例。  
  
 ModelBus 引用了此 DSL 现在即可解决在文本模板并在普通的代码。  
  
#### 构造使用 ModelBus 的一个 DSL 引用字段的特性  
  
1.  使用最小的语言解决方案模板，创建一个新的 DSL。  命名该语言 MBConsumer 并将文件扩展名设置为 “.consume”。  
  
2.  在 DSL 项目中，添加对 MBProvider DSL 程序集。  右击 `MBConsumer\Dsl\References` 然后单击 **添加引用**。  在 **浏览** 选项，找到 `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     这使您可以创建使用另一个 DSL 的代码。  如果要创建对多个 DSL，还添加它们。  
  
3.  在 DSL 定义关系图，请右击关系图然后单击 **启用 ModelBus**。  在对话框中，选择 **使此 DSL 使用 ModelBus**。  
  
4.  在类 `ExampleElement`，请在 " 属性 " 窗口中添加一个新字段的属性 `MBR`，并且，将其类型设置为 `ModelBusReference`。  
  
5.  右击关系图的字段的特性然后单击 **编辑 ModelBusReference 特定属性**。  在对话框中，选择 **一个模型元素**。  
  
     设置文件对话框筛选器将以下内容。  
  
     `Provider File|*.provide`  
  
     在子字符串 “&#124;”是文件选择对话框中的筛选器。  使用 \*.\*，您可以将它允许任意文件  
  
     在 **模型元素类型** 列表中，输入一矿石的名称多个字段类在提供程序 DSL \(例如， Company.MBProvider.Task\)。  它们可以是抽象类。  如果保留空白列表，用户可将对所有元素。  
  
6.  关闭对话框并 **转换所有模板**。  
  
 您创建了可能包含对另一个 DSL 的元素的一个 DSL。  
  
#### 创建 ModelBus 引用添加到解决方案中的其他文件  
  
1.  在 MBConsumer 解决方案，请按 CTRL\+F5。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的实验实例。 **MBConsumer\\Debugging** 项目打开。  
  
2.  添加 Sample.provide 的复制到 **MBConsumer\\Debugging** 项目。  ，因为 ModelBus 引用必须引用同一解决方案，的文件这是必需的。  
  
    1.  右击调试项目，指向 **添加**，然后单击 **现有项目**。  
  
    2.  在 **添加项目** 对话框中，将筛选器将 **所有文件 \(\*.\*\)**。  
  
    3.  导航到 `MBProvider\Debugging\Sample.provide` 然后单击 **添加**。  
  
3.  打开 `Sample.consume`。  
  
4.  单击一个示例形状，然后在 " 属性 " 窗口中，在 MBR 单击属性 **\[...\]** 。  在对话框中，单击 **浏览** 并选择 `Sample.provide`。  在元素窗口中，展开该类型任务并选择一个元素。  
  
5.  保存该文件。  
  
     \(不要关闭 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的实验实例。\)  
  
 您创建了一个包含 ModelBus 对另一个模型中的元素的模型。  
  
#### 解决 ModelBus 对文本模板  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的实验实例中，打开示例文本模板文件。  如下所示设置其内容。  
  
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
  
    1.  必须设置 `template` 指令的 `hostSpecific` 和 `inherits` 属性。  
  
    2.  使用者模型来访问以常规方式通过在该 DSL 生成的指令处理器。  
  
    3.  程序集和导入指令必须能够访问 ModelBus 和提供程序 DSL 的类型。  
  
    4.  如果您知道许多 MBR 与同一模型链接，调用 CreateAdapter 只有一个最好。  
  
2.  保存模板。  验证生成的文本文件类似于以下内容。  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### 解决 ModelBus 引用在笔势处理程序  
  
1.  ，则运行，结束 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的实验实例。  
  
2.  添加一个名为 MBConsumer \\Dsl\\Custom .cs 并将其设置为以下内容的文件。  
  
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
  
3.  按 Ctrl\+F5。  
  
4.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的实验实例中，打开 `Debugging\Sample.consume`。  
  
5.  双击一个形状。  
  
     如果将该元素的 MBR，被引用的方式打开，并被引用的元素中选择。  
  
## 请参阅  
 [通过使用 Visual Studio Modelbus 集成模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)