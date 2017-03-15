---
title: "通过使用 Visual Studio Modelbus 集成模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 26
---
# 通过使用 Visual Studio Modelbus 集成模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 提供了用于创建模型之间和来自其他工具链接到模型的方法。 例如，您可以链接域特定语言 \(DSL\) 模型和 UML 模型。 您可以创建一组集成的 Dsl。  
  
 ModelBus 允许你创建到模型或模型内部的特定元素的唯一引用。 此引用可以存储在模型外部例如，在另一个模型中的元素。 当在随后的场合，一种工具想要获取元素的访问时，模型总线基础结构将加载相应的模型，并返回的元素。 如果您希望，您可以向用户显示该模型。 如果该文件不能访问在以前的位置，ModelBus 将要求用户能够找到它。 如果用户找到该文件，则 ModelBus 将修复对该文件的所有引用。  
  
> [!NOTE]
>  在当前 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus，链接的模型的实现必须是在同一个项 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案。  
  
 有关其他信息和示例代码，请参阅︰  
  
-   [如何：添加拖放处理程序](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Visual Studio 的建模 SDK](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> 提供对 DSL 的访问  
 您可以创建对模型或其元素的 ModelBus 引用之前，您必须为 DSL 定义 ModelBusAdapter。 若要这样做的最简单方法是使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模型总线扩展，将命令添加到 DSL 设计器。  
  
###  <a name="expose"></a> 若要公开 DSL 定义向模型总线  
  
1.  下载并安装 Visual Studio 模型总线扩展，除非您已经安装它。 有关详细信息，请参阅 [可视化和建模 SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
2.  打开 DSL 定义文件。 右键单击设计图面，然后单击 **启用 Modelbus**。  
  
3.  在对话框中，选择 **我想要向 ModelBus 公开此 DSL**。 如果您希望此 DSL 同时公开其模型以及使用对其他 Dsl 的引用，可以选择这两个选项。  
  
4.  单击“确定”。 新项目"ModelBusAdapter"添加到 DSL 解决方案。  
  
5.  如果你想要从文本模板访问 DSL，则必须在新项目中修改 AdapterManager.tt。 如果你想要从其他代码如命令和事件处理程序访问 DSL，则忽略此步骤。 有关详细信息，请参阅[在文本模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
    1.  更改到 AdapterManagerBase 的基类 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。  
  
    2.  该文件的末尾插入此附加特性类 AdapterManager 的前面︰  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  在 ModelBusAdapter 引用项目中，添加 **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**。  
  
     如果您想要从文本模板和其他代码访问 DSL，则需要两个适配器，一个修改，一个不被修改。  
  
6.  单击 **转换所有模板**。  
  
7.  重新生成解决方案。  
  
 现 modelbus 可以打开此 DSL 的实例。  
  
 该文件夹 `ModelBusAdapters\bin\*` 包含由生成的程序集 `Dsl` 项目和 `ModelBusAdapters` 项目。 若要从另一个 DSL 引用此 DSL，应先导入这些程序集。  
  
### 确保元素可被引用  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 适配器使用元素的 guid 来标识它，默认情况下。 因此，这些标识符都必须保留在模型文件。  
  
##### 若要确保保留 Id 元素  
  
1.  打开 DslDefinition.dsl。  
  
2.  在 DSL 资源管理器中，展开 **Xml 序列化行为**, ，然后 **类数据**。  
  
3.  对于每个类，你想要创建模型总线引用︰  
  
     单击类节点，然后在属性窗口中，确保 **序列化 Id** 设置为 `true`。  
  
 或者，如果您想要使用元素名称来标识元素而不是 guid，您可以重写生成的适配器的部分。 重写中的适配器类的以下方法︰  
  
-   重写 `GetElementId` 可返回你想要使用的标识符。 在创建引用时，调用此方法。  
  
-   重写 `ResolveElementReference` 来查找从模型总线引用正确的元素。  
  
##  <a name="editRef"></a> 从另一个 DSL 访问 DSL  
 可以将模型总线引用存储在域属性中 DSL，并且您可以编写使用它们的自定义代码。 您还可以让用户通过选取模型文件和其中的元素创建模型总线引用。  
  
 若要允许 DSL 使用对另一个 DSL 的引用，您应首先使它 *使用者* 模型总线引用。  
  
#### 若要允许 DSL 使用对公开的 DSL 的引用  
  
1.  在 DSL 定义关系图中，右键单击关系图的主要部分，然后单击 **启用 Modelbus**。  
  
2.  在对话框中，选择 **我想要启用此模型使用模型总线引用**。  
  
3.  在使用 DSL 的 Dsl 项目中，将以下程序集添加到项目引用。 您将公开的 DSL 的 ModelBusAdapter\\bin\\ \* 目录中找到这些程序集 （.dll 文件）。  
  
    -   公开的 DSL 程序集，例如 **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   公开的模型总线适配器程序集，例如 **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  将以下.NET 程序集添加到使用 DSL 项目的项目引用。  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### 若要将模型总线引用存储在域属性  
  
1.  在使用 DSL 的 DSL 定义中，将域属性添加到域类并设置其名称。  
  
2.  在属性窗口中，选择，域属性设置 **类型** 到 `ModelBusReference`。  
  
 在此阶段，程序代码可以设置属性值，但它在属性窗口中是只读的。  
  
 您可以允许用户使用专用 ModelBus 引用编辑器设置属性。 有两个版本的此编辑器或 *选取器︰* 一个允许用户选择模型文件和其他允许用户选择模型文件和模型中的某个元素。  
  
#### 若要允许用户在域属性中设置模型总线引用  
  
1.  右键单击域属性，然后单击 **编辑 ModelBusReference 特定属性**。 会打开一个对话框。 这是 *模型总线选取器*。  
  
2.  选择相应 **种 ModelBusReference**︰ 对模型或模型中的元素。  
  
3.  在文件对话框筛选器字符串中，输入一个字符串，例如 `Family Tree files |*.ftree`。 替换公开的 DSL 的文件扩展名。  
  
4.  如果您选择引用模型中的元素，可以添加类型的列表，用户可以从中选择，例如 Company.FamilyTree.Person。  
  
5.  单击 **确定**, ，然后单击 **转换所有模板** 在解决方案资源管理器工具栏中。  
  
    > [!WARNING]
    >  如果尚未选择有效的模型或实体，确定按钮将不起作用，即使它可能看起来已启用。  
  
6.  如果指定的目标类型 （如 company.familytree.person） 的列表，然后您必须将添加到 DSL 项目中，程序集引用引用目标 DSL，例如 Company.FamilyTree.Dsl.dll DLL  
  
#### 若要测试模型总线引用  
  
1.  构建公开和使用 Dsl。  
  
2.  通过按 F5 或 CTRL \+ F5 在实验模式下运行一个 Dsl。  
  
3.  在实验实例中的调试项目 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，添加的每个 DSL 实例的文件。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 只能解析对模型中相同的项的引用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案。 例如，您无法创建对模型文件的引用中的文件系统其他部分。  
  
4.  在公开的 DSL 的实例中创建一些元素和链接并将其保存。  
  
5.  打开使用 DSL 的实例并选择一个具有模型总线引用属性的模型元素。  
  
6.  在属性窗口中，双击模型总线引用属性。 选取器对话框随即打开。  
  
7.  单击 **浏览** 然后选择公开的 DSL 的实例。  
  
     选取器还将允许您选择的项在模型中，如果指定的模型总线引用的特定元素的类型。  
  
## 在程序代码中创建的引用  
 如果您想要存储对模型或模型中的元素的引用，则创建 `ModelBusReference`。 有两种类型的 `ModelBusReference`︰ 模型引用和元素的引用。  
  
 若要创建模型引用，您需要该模型的一个实例，以及的文件名的 DSL 的 AdapterManager 或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模型的项目项。  
  
 若要创建元素引用，您需要一个适配器模型文件，以及想要引用的元素。  
  
> [!NOTE]
>  与 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus，您可以在同一个创建仅对项的引用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案。  
  
### 导入公开的 DSL 程序集  
 在使用的项目中，添加对公开的 DSL 的 DSL 和 ModelBusAdapter 程序集的项目引用。  
  
 例如，假设你想要将 ModelBus 引用存储在 MusicLibrary DSL 的元素。 ModelBus 引用将引用 FamilyTree DSL 的元素。 在 `Dsl` MusicLibrary 解决方案，在引用节点中的项目添加对下列程序集的引用︰  
  
-   Fabrikam.FamilyTree.Dsl.dll\-公开的 DSL。  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll\-公开的 DSL 的 ModelBus 适配器。  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 在找不到这些程序集 `ModelBusAdapters` 公开的 DSL 项目下 `bin\*`。  
  
 将在其中创建引用代码文件中，通常需要导入这些命名空间︰  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### 若要创建到模型引用  
 若要创建模型引用，可以访问用于公开的 DSL 的 AdapterManager 并使用它来创建到模型的引用。 您可以指定文件路径或 `EnvDTE.ProjectItem`。  
  
 可以从 AdapterManager 中获取适配器，它提供访问的模型中的各个元素。  
  
> [!NOTE]
>  已完成后，必须释放适配器。 若要实现此目的的最简便方法是使用 `using` 语句。 下面的示例阐释了这一点。  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 如果您想要能够使用 `modelReference` 更高版本，您可以将其存储在具有外部类型的域属性 `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 若要允许用户编辑此域属性，请使用 `ModelReferenceEditor` 用作编辑器特性中的参数。 有关详细信息，请参阅 [允许用户编辑引用](#editRef)。  
  
### 若要创建的元素引用  
 为模型创建的适配器可以用于创建和解析引用。  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 如果您想要能够使用 `elementReference` 更高版本，您可以将其存储在具有外部类型的域属性 `ModelBusReference`。 若要允许用户对其进行编辑，请使用 `ModelElementReferenceEditor` 用作编辑器特性中的参数。 有关详细信息，请参阅 [允许用户编辑引用](#editRef)。  
  
### 解析的引用  
 如果您有 `ModelBusReference` \(MBR\) 可以获取模型或它所引用的模型元素。 如果元素存在上一个关系图或其他视图中，您可以打开该视图并选择元素。  
  
 可以从 MBR 创建适配器。 从适配器，您可以获取模型的根。 您还可以处理引用的模型中的特定元素的 Mbr。  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### 若要解决文本模板中的 ModelBus 引用  
  
1.  您想要访问的 DSL 必须具有通过文本模板配置为访问 ModelBus 适配器。 有关更多信息，请参见[提供对 DSL 的访问](#provide)。  
  
2.  通常情况下，您需要访问 DSL 使用模型总线引用 \(MBR\) 存储在源 DSL 的目标。 因此，模板包括源 DSL，再加上代码指令，用于解析 MBR。 有关文本模板的详细信息，请参阅 [从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 有关详细信息和演练，请参阅 [在文本模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## 序列化 ModelBusReference  
 如果您想要存储 `ModelBusReference` \(MBR\) 中以字符串的形式，您可以将其序列化︰  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 在这种方式中序列化的 MBR 与上下文无关。 如果使用的简单的基于文件的模型总线适配器，则 MBR 将包含绝对文件路径。 这足以如果实例模型文件永不移动。 但是，模型文件通常会中的项 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目。 用户希望能够将整个项目移动到文件系统的不同部分。 他们还希望能够保留在源代码管理下的项目，然后在不同计算机上打开它。 因此应相对于项目中包含的文件的位置序列化路径名称。  
  
### 序列化相对于指定的文件路径  
 一个 `ModelBusReference` 包含 `ReferenceContext`, ，这是一个可以在其中存储信息，如文件路径相对于其应序列化的字典。  
  
 要序列化相对于路径︰  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 若要从字符串检索引用︰  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### 由其他适配器创建的 ModelBusReferences  
 以下信息是您想要创建自己的适配器的情况下很有用。  
  
 一个 `ModelBusReference` \(MBR\) 由两部分组成︰ 由模型总线反序列，MBR 标头和特定于适配器的特定适配器管理器处理。 这样可以提供您自己的适配器序列化格式。 例如，可以引用数据库，而不是一个文件，或者您可以在适配器引用中存储的其他信息。 您自己的适配器可以放置中的其他信息 `ReferenceContext`。  
  
 当您反序列化 MBR 时，必须提供的然后存储在 MBR 对象中的 ReferenceContext。 当序列化 MBR 时，存储的 ReferenceContext 使用适配器来帮助生成字符串。 反序列化的字符串不包含 ReferenceContext 中的所有信息。 例如，在简单的基于文件的适配器中，ReferenceContext 包含根文件路径，它不会存储在序列化的 MBR 字符串。  
  
 MBR 进行反序列化以两个阶段︰  
  
-   `ModelBusReferencePropertySerializer` 是处理 MBR 标头的标准序列化程序。 它使用标准 DSL `SerializationContext` 属性包，存储在 `ReferenceContext` 使用密钥 `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`。 具体而言， `SerializationContext` 应包含的一个实例 `ModelBus`。  
  
-   ModelBus 适配器将处理与 MBR 的特定于适配器的部分。 它可以使用存储在 MBR 的 ReferenceContext 中的其他信息。 简单的基于文件的适配器保留根文件路径使用键 `FilePathLoadContextKey` 和 `FilePathSaveContextKey`。  
  
     仅当它使用反序列化模型文件中的适配器引用。  
  
## 若要创建模型  
  
### 创建、 打开和编辑模型  
 以下片段摘自 VMSDK 网站上进行的状态机示例。 它阐释了使用 ModelBusReferences 创建和打开模型，并获取与模型关联的关系图。  
  
 在此示例中，目标 DSL 的名称是 StateMachine。 多个名称从中派生，例如模型类的名称和 ModelBusAdapter 的名称。  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## 验证引用  
 BrokenReferenceDetector 测试可保留 ModelBusReferences 的存储区中的所有域属性。 调用该操作您提供在其中找到任何操作。 这是对于验证方法尤为有用。 下面的验证方法测试尝试保存该模型上的存储，并报告错误窗口中的损坏的引用︰  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## 由 ModelBus 扩展执行的操作  
 以下信息不重要，但如果进行大量使用 ModelBus 可能很有用。  
  
 ModelBus 扩展 DSL 解决方案中进行以下更改。  
  
 右键单击 DSL 定义关系图时，请单击 **启用 Modelbus**, ，然后选择 **允许此 DSL 使用 ModelBus**:  
  
-   在 DSL 项目的引用添加到 **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   在 DSL 定义中，添加外部类型引用︰ `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`。  
  
     您可以看到在引用 **DSL 资源管理器**, 下 **域类型**。 若要手动添加外部类型引用，请右键单击根节点。  
  
-   添加新的模板文件，则 **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**。  
  
 当您设置域属性的类型为 modelbusreference 后，然后右键单击该属性并单击 **启用 ModelBusReference 特定属性**:  
  
-   多个 CLR 特性将添加到域属性。 在属性窗口的自定义属性字段中，您可以看到它们。 在 **Dsl\\GeneratedCode\\DomainClasses.cs**, ，您可以看到这些属性在属性声明︰  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 当您右键单击 DSL 定义关系图时，请单击 **启用 ModelBus**, ，然后选择 **向 ModelBus 公开此 DSL**:  
  
-   一个新项目 `ModelBusAdapter` 添加到解决方案。  
  
-   对引用 `ModelBusAdapter` 添加到 `DslPackage` 项目。`ModelBusAdapter` 具有对引用 `Dsl` 项目。  
  
-   在 **DslPackage\\source.extention.tt**, ，`|ModelBusAdapter|` 添加为 MEF 组件。  
  
## 请参阅  
 [如果：在程序代码中从文件打开模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [将 UML 模型与其他模型和工具集成](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [如何：添加拖放处理程序](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [在文本模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)