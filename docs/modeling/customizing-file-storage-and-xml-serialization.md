---
title: "自定义文件存储和 XML 序列化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.xmlbehavior"
helpviewer_keywords: 
  - "域特定语言，序列化"
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# 自定义文件存储和 XML 序列化
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当用户保存实例，或 *模型*, ，域特定语言 (DSL) 中的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，创建或更新的 XML 文件。 可以重新加载文件以重新创建存储区中的模型。  
  
 可以通过调整下的设置来自定义序列化方案 **Xml 序列化行为** DSL 资源管理器中。 没有下的节点 **Xml 序列化行为** 为每个域类、 属性和关系。 关系都位于其源类下。 也有对应于形状、 连接器和关系图类节点。  
  
 你还可以编写更多高级自定义项的程序代码。  
  
> [!NOTE]
>  如果你想要将模型保存为特定的格式，但不是需要从该窗体重新加载它，请考虑使用文本模板的模型，而不是自定义序列化方案从生成输出。 有关详细信息，请参阅 [从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
## <a name="model-and-diagram-files"></a>模型和关系图文件  
 每个模型通常保存在两个文件︰  
  
-   模型文件有一个名称，如 **Model1.mydsl**。 它将存储的模型元素和关系和它们的属性。 文件扩展名，例如 **.mydsl** 由 **FileExtension** 属性 **编辑器** DSL 定义中的节点。  
  
-   关系图文件有一个名称，如 **Model1.mydsl.diagram**。 它将存储形状、 连接器，和它们的位置、 颜色、 线厚度和关系图的外观的其他详细信息。 如果用户删除 **.diagram** 文件，在模型中的基本信息不会丢失。 仅关系图的布局将丢失。 当打开模型文件时，一组默认的形状并将创建连接器。  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>若要更改文件扩展名的 DSL  
  
1.  打开 DSL 定义。 在 DSL 资源管理器，单击编辑器节点。  
  
2.  在属性窗口中，编辑 **FileExtension** 属性。 不包括初始"。"的文件扩展名。  
  
3.  在解决方案资源管理器，更改中的两个项模板文件的名称 **DslPackage\ProjectItemTemplates**。 这些文件具有遵循以下格式的名称︰  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>默认序列化方案  
 若要创建一个用于本主题的示例，使用以下 DSL 定义。  
  
 ![DSL 定义关系图 &#45;王朝家谱模型](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 此 DSL 用于创建在屏幕具有以下外观的模型。  
  
 ![家谱关系图、工具箱和资源管理器](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 此模型进行保存，然后重新在 XML 文本编辑器中打开它︰  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 请注意有关序列化模型的以下几点︰  
  
-   每个 XML 节点具有与域类名，相同的名称，只是初始字母为小写。 例如， `familyTreeModel` 和 `person`。  
  
-   域属性，如名称和 BirthYear 扩展会序列化为 XML 节点中的属性。 同样，将属性名称的初始字符转换为小写。  
  
-   每个关系序列化为 XML 节点嵌套在关系的源端。 该节点具有相同名称，为源角色属性，但大小写的初始字符。  
  
     例如，在 DSL 定义中，名为的角色 **人员** 源自在 **FamilyTree** 类。  在 XML 中，它通过名为的节点中表示 `people` 嵌套在 `familyTreeModel` 节点。  
  
-   每个嵌入的关系的目标端序列化为嵌套在关系的节点。 例如， `people` 节点包含若干 `person` 节点。  
  
-   每个引用关系的目标端序列化为 *标记*, ，这将编码目标元素的引用。  
  
     例如，在 `person` 节点，可以有 `children` 关系。 此节点包含名字对象，例如︰  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>了解名字对象  
 名字对象用于表示的模型和关系图文件不同部分之间的交叉引用。 它们也用在 `.diagram` 文件来指代模型文件中的节点。 有两种形式的名字对象︰  
  
-   *Id 名字对象* quote 目标元素的 GUID。 例如：  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *限定密钥名字对象* 通过称为标记密钥指定的域属性的值标识的目标元素。 目标元素的名字对象是由其父元素的嵌入关系树中的名字对象的前缀。  
  
     下面的示例将从有在其中 DSL 是一个名为唱片集，具有类命名首歌曲关系嵌入到域的域类︰  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     如果目标类具有为其域属性，则将使用限定密钥名字对象选项 **名字对象键** 设置为 `true` 中 **Xml 序列化行为**。 在示例中，此选项设置为"唱片集"和"歌曲"的域类中名为"Title"域属性。  
  
 限定密钥名字对象更易于读取比 ID 名字对象。 如果你想要的人员无法读取模型文件的 XML，请考虑使用限定密钥名字对象。 但是，它是用户可以设置多个元素可以有相同的名字对象键。 重复的键可能会导致文件无法正确地重新加载。 因此，如果你定义使用限定密钥名字对象引用的域类，则应考虑阻止用户保存具有重复的名字对象的文件的方式。  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>若要设置域类，将引用的 ID 名字对象  
  
1.  请确保 **名字对象键** 是 `false` 每个域中为属性类和基类。  
  
    1.  DSL 资源管理器，展开 **Xml 序列化 Behavior\Class 数据\\***\< 域类>***\Element 数据**。  
  
    2.  验证 **名字对象键** 是 `false` 对于每个域属性。  
  
    3.  如果域类具有的基的类，请重复该类中的过程。  
  
2.  设置 **序列化 Id** = `true` 域类。  
  
     此属性可以下找到 **Xml 序列化行为**。  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>若要设置域类，将引用的限定密钥名字对象  
  
-   设置 **名字对象键** 现有域类域属性。 属性的类型必须是 `string`。  
  
    1.  DSL 资源管理器，展开 **Xml 序列化 Behavior\Class 数据\\***\< 域类>***\Element 数据**, ，然后选择域属性。  
  
    2.  在属性窗口中，设置 **名字对象键** 到 `true`。  
  
-   \- 或-  
  
     创建新的域类使用 **名为域类** 工具。  
  
     此工具创建具有一个名为名称的域属性的新类。  **是元素名称** 和 **名字对象键** 此域属性的属性初始化为 `true`。  
  
-   \- 或-  
  
     与具有名字对象键属性的另一个类，从域类中创建一个继承关系。  
  
### <a name="avoiding-duplicate-monikers"></a>避免重复的名字对象  
 如果你使用限定密钥名字对象，则可能在用户的模型中的两个元素，无法键属性中有相同的值。 例如，如果 DSL 具有类具有一个属性名称的人员，用户可以设置的两个元素的名称相同。 虽然该模型可能是保存到文件，它将不重新加载正确。  
  
 有几种方法，可帮助避免这种情况︰  
  
-   设置 **是元素名称** = `true` 密钥域属性。 选择 DSL 定义关系图上的域属性，然后在属性窗口中设置值。  
  
     当用户创建的类的新实例时，此值会导致自动分配一个不同的值的 domain 属性。 默认行为的类名称的末尾添加一个数字。 这不会阻止用户的名称更改为有重复，但它有助于在情况下用户在保存模型之前未设置的值。  
  
-   启用 DSL 的验证。 DSL 资源管理器，在选择 Editor\Validation，并设置 **...使用** 属性设置为 `true`。  
  
     没有多义性检查自动生成的验证方法。 该方法是在 `Load` 验证类别。 这样可以确保，用户会收到警告，它可能无法重新打开该文件。  
  
     有关详细信息，请参阅 [域特定语言中的验证](../modeling/validation-in-a-domain-specific-language.md)。  
  
### <a name="moniker-paths-and-qualifiers"></a>名字对象路径和限定符  
 限定的密钥标记结束与名字对象的键，并带有嵌入的树中其父代的标记前缀。 例如，如果唱片集的名字对象为︰  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 那么该唱片集中歌曲之一可能为︰  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 但是，如果专辑改为引用的 ID，然后名字对象将，如下所示︰  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 请注意，GUID 是唯一的因为它从不前缀由其父级的名字对象。  
  
 如果你知道特定域属性，将始终具有一个模型中的唯一值，则可以设置 **是名字对象限定符** 到 `true` 该属性。 这将导致它要用作限定符，而无需使用的父标记。 例如，如果同时设置 **是名字对象限定符** 和 **名字对象键** 唱片集类的标题域属性，该模型的名称或标识符中不使用名字对象为唱片集及其嵌入的子级︰  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>自定义 XML 的结构  
 若要进行以下自定义，展开 **Xml 序列化行为** DSL 资源管理器中的节点。 下的域类中，展开若要查看的属性和关系，以指明其出处的此类在列表的元素数据节点。 选择一个关系，并调整其属性窗口中的选项。  
  
-   设置 **省略元素** 为 true，若要省略源角色节点，只需目标元素的列表。 如果源和目标类之间没有多个关系，不应设置此选项。  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   设置 **使用完整的窗体** 将目标节点嵌入节点表示关系实例。 域属性添加到域关系时，将自动设置此选项。  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   设置 **表示** = **元素** 为具有域属性保存与某一元素，而不是作为属性值。  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   若要更改在其中属性和关系进行序列化的顺序，右键单击受元素数据的项，并使用 **移** 或 **下移** 菜单命令。  
  
## <a name="major-customization-using-program-code"></a>使用程序代码的主要自定义项  
 你可以将部分或全部的序列化算法。  
  
 我们建议你先研究中的代码 **Dsl\Generated Code\Serializer.cs** 和 **SerializationHelper.cs**。  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>若要自定义特定类的序列化  
  
1.  设置 **是自定义** 中的节点下该类 **Xml 序列化行为**。  
  
2.  转换所有模板生成该解决方案，然后调查生成编译错误。 接近每个错误的注释说明了你必须提供哪些代码。  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>若要提供自己的整个模型的序列化  
  
1.  重写中 Dsl\GeneratedCode\SerializationHelper.cs 方法  
  
## <a name="options-in-xml-serialization-behavior"></a>Xml 序列化行为中的选项  
 DSL 资源管理器，在 Xml 序列化行为节点包含每个域类、 关系、 形状、 连接器和关系图类的子节点。 在每个这些节点是的属性和关系源于该元素的列表。 在其自己右和下它们的源类表示关系。  
  
 下表总结了你可以在此部分的 DSL 定义中设置的选项。 在每个情况下，在 DSL 资源管理器，选择某个元素和设置属性窗口中的选项。  
  
### <a name="xml-class-data"></a>Xml 类数据  
 在下的 DSL 资源管理器中找到这些元素 **Xml 序列化 Behavior\Class 数据**。  
  
|||  
|-|-|  
|属性|描述|  
|具有自定义元素的架构|如果为 True，指示域类具有自定义元素的架构|  
|为自定义|将其设置为 **True** 如果你想要编写此域类自己序列化和反序列化代码。<br /><br /> 生成解决方案并调查要发现的详细的说明的错误。|  
|域类|此类数据节点应用到的域类。 只读。|  
|元素名称|此类的元素的 Xml 节点名称。 默认值为域类名称的小写版本。|  
|名字对象属性名称|标记元素以包含引用的属性的名称。 如果保留为空，则使用的键属性或 id 的名称。<br /><br /> 在此示例中，它是"name":  `<personMoniker name="/Mike Nash"/>`|  
|标记元素名称|用于引用此类的元素的名字对象的 xml 元素的名称。<br /><br /> 默认值为"标记"后缀的类名称的小写版本。 例如 `personMoniker`。|  
|标记类型名称|为此类的元素的名字对象生成的 xsd 类型的名称。 XSD 处于 **Dsl\Generated 代码\\\*Schema.xsd**|  
|序列化 Id|如果为 True，在文件中包含该元素 GUID。 这必须是 true，如果没有任何属性标记为可供 **名字对象键** 和 DSL 定义与此类的引用关系。|  
|类型名称|在指定的域类从 xsd 中生成的 xml 类型的名称。|  
|备注|与此元素关联的非正式说明|  
  
### <a name="xml-property-data"></a>Xml 属性数据  
 在类节点下找到 Xml 属性节点。  
  
|||  
|-|-|  
|属性|描述|  
|域属性|Xml 序列化配置数据应用的属性。 只读。|  
|是标记密钥|如果为 True，则属性用作创建引用此域类的实例的名字对象的键。|  
|是标记限定符|如果为 True，该属性用于创建限定符名字对象中。 如果为 false，和 SerializeId 未得到满足此域类，名字对象被限定中嵌入的树的父元素的标记。|  
|表示形式|如果属性，该属性序列化为 xml 特性;如果元素，它是序列化为的元素;如果忽略，则不序列化。|  
|Xml 名称|用于 xml 特性或元素表示的属性的名称。 默认情况下，这是域的属性名称的小写版本。|  
|备注|与此元素关联的非正式说明|  
  
### <a name="xml-role-data"></a>Xml 角色的数据  
 角色数据节点的源类节点下找到。  
  
|属性|描述|  
|--------------|-----------------|  
|具有自定义标记|设置为 true，如果你想要提供自己的代码生成和解决遍历此关系的名字对象。<br /><br /> 有关详细说明，构建解决方案，，然后双击的错误消息。|  
|域关系|指定要应用这些选项的关系。 只读。|  
|省略元素|如果为 true，架构中省略对应的源角色的 XML 节点。<br /><br /> 如果源和目标类之间没有多个关系，此角色节点会区分属于两个关系的链接。 因此，我们建议，未设置此选项在此情况下。|  
|角色元素名称|指定派生自的源角色的 XML 元素的名称。 默认值为角色属性名称。|  
|使用完整的窗体|如果为 true，每个目标元素或标记括在 XML 节点表示关系中。 这应设置为 true，如果关系具有其自己的域属性。|  
  
## <a name="see-also"></a>请参阅  
 [导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)