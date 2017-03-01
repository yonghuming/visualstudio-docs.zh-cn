---
title: "T4 文本模板编写准则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 9
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 7d9dd7193455a625b0410eaca3b2bd243c109743
ms.lasthandoff: 02/22/2017

---
# <a name="guidelines-for-writing-t4-text-templates"></a>T4 文本模板编写准则
以下常规准则可能会有所帮助，如果您生成程序代码或在其他应用程序资源[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它们不被固定的规则。  
  
## <a name="guidelines-for-design-time-t4-templates"></a>设计时 T4 模板的准则  
 设计时 T4 模板是模板，在其中生成代码您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在设计时的项目。 有关详细信息，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 生成的应用程序的变量部分。  
 代码生成是应用的最适用于在项目过程中可能会更改或将更改应用程序的不同版本之间程序的那些方面。 这些变量部分分开更固定的方面的以便您可以更轻松地确定要生成的具有。 例如，如果您的应用程序提供了一个网站，独立标准的页面服务函数的定义从一个页面到另一个页面的导航路径的逻辑。  
  
 对一个或多个源模型中的变量部分进行编码。  
 模型是代码的文件或数据库的每个模板都可以读取以获得特定值的变量部分的要在生成。 模型可以是数据库、 设计、 关系图，或域特定语言的 XML 文件。 通常情况下，一个模型用于生成中的文件多[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目。 从单独的模板生成每个文件。  
  
 您可以在项目中使用多个模型。 例如，可以定义 Web 页，以及单独的页面布局的模型之间的导航模型。  
  
 将模型的侧重点上用户的需求和词汇，不是根据您的实现。  
 例如，在网站应用程序中，您将希望模型来指代网页和超链接。  
  
 理想情况下，选择一种形式的演示文稿，适合这种模型表示的信息。 例如，通过网站的导航路径的模型可能是框和箭头的关系图。  
  
 测试生成的代码。  
 使用手动或自动测试来验证生成的代码按用户所需的方式工作。 避免从同一模型从其生成的代码生成测试。  
  
 在某些情况下，可以直接在模型上执行常规测试。 例如，您可以编写测试，以确保从任何其他的导航可以到达 Web 站点中的每一页。  
  
 允许自定义代码︰ 生成分部类。  
 允许您手动编写此外到生成的代码的代码。 很少的代码生成架构，以便能够解决所有可能的变体可能产生的。 因此，您应会将添加到或重写某些生成的代码。 在生成的材料处于一种.NET 语言如[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，两种策略是特别有用︰  
  
-   生成的类应为部分。 这样就可以将内容添加到生成的代码。  
  
-   成对使用，继承自另一个应生成类。 类的基类应包含所有生成的方法和属性，并且派生的类应包含仅的构造函数。 这允许您手动编写的代码重写任何生成的方法。  
  
 在诸如 XML 等其他生成的语言，使用`<#@include#>`指令即可使手工编写和生成内容的简单组合。 在更复杂的情况下，您可能必须编写后续处理步骤将生成的文件与用手编写的任何文件组合在一起。  
  
 将通用材料移动到包含文件或运行时模板  
 为了避免重复类似的文本块和多个模板中的代码，使用`<#@ include #>`指令。 有关详细信息，请参阅[T4 包含指令](../modeling/t4-include-directive.md)。  
  
 您可以还生成一个单独的项目中的运行时文本模板，然后将它们调用从设计时模板。 若要执行此操作，请使用`<#@ assembly #>`指令，以便访问单独的项目。 有关示例，请参阅["继承在文本模板"Gareth Jones 博客中](http://go.microsoft.com/fwlink/?LinkId=208373)。  
  
 考虑将较大的代码块移动到单独的程序集中。  
 如果您具有大型代码块和类功能块，则可能需要将一些这段代码移动到方法中，在一个单独的项目中编译。 您可以使用`<#@ assembly #>`指令，以便访问在模板中的代码。 有关详细信息，请参阅[T4 程序集指令](../modeling/t4-assembly-directive.md)。  
  
 可以将方法放在该模板可以继承一个抽象类。 抽象类必须从<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>。</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>继承 有关详细信息，请参阅[T4 模板指令](../modeling/t4-template-directive.md)。  
  
 生成的代码，不是配置文件  
 编写变量的应用程序的一种方法是编写接受配置文件的通用程序代码。 以这种方式编写的应用程序非常灵活，并且可以时业务需求发生变化，而无需重新生成应用程序重新配置。 但是，此方法的缺点是应用程序将执行效果不如更具体的应用程序。 此外，它的程序代码将更难以阅读和维护，部分原因是因为它必须始终处理最一般的类型。  
  
 与此相反，在编译之前生成的可变部分的应用程序可以为强类型。 这样，就容易得多且更可靠地编写用手编写代码，并将其与生成集成该软件的部分。  
  
 若要获取代码生成的全部好处，请尝试生成程序代码而不是配置文件。  
  
 使用生成的代码的文件夹  
 将模板和生成的文件放在一个名为的项目文件夹**生成的代码**若要让其清除，这不应直接编辑的文件。 如果您创建自定义代码来覆盖或添加到生成的类，将这些类放在名为的文件夹**自定义代码**。 典型的项目中的结构如下所示︰  
  
```  
MyProject  
   Custom Code  
      Class1.cs  
      Class2.cs  
   Generated Code  
      Class1.tt  
          Class1.cs  
      Class2.tt  
          Class2.cs  
   AnotherClass.cs  
  
```  
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>运行时 （预处理） T4 模板的准则  
 将通用材料移到继承的模板  
 可以使用继承共享方法和 T4 文本模板之间的文本块。 有关详细信息，请参阅[T4 模板指令](../modeling/t4-template-directive.md)。  
  
 您还可以使用包含具有运行时模板文件。  
  
 移动大型代码体转换为分部类。  
 每个运行时模板生成模板同名的分部类定义。 您可以编写包含同一个类的另一个部分定义的代码文件。 可以对这种方式中的类添加方法、 字段和构造函数。 可以从模板中的代码块调用这些成员。  
  
 执行此操作的一个优点是代码会更容易编写，因为将使用 IntelliSense。 此外，您可以获得更好地分离演示文稿和基础的逻辑。  
  
 例如，在**MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 在**MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 允许自定义代码︰ 提供扩展点  
 请考虑生成中的虚方法\<#+ 类功能块 #&1;>。 这允许单个模板可以在无需修改即可在很多环境中使用。 而不是修改模板，您可以构建派生的类，它提供的最小的附加逻辑。 派生的类可以是常规代码，也可以是运行时模板。  
  
 例如，在 MyStandardRunTimeTemplate.tt:  
  
```  
This page is copyright <#= CompanyName() #>.  
<#+ protected virtual string CompanyName() { return ""; } #>  
```  
  
 在应用程序代码中︰  
  
```  
class FabrikamTemplate : MyStandardRunTimeTemplate  
{  
  protected override string CompanyName() { return "Fabrikam"; }  
}  
...  
  string PageToDisplay = new FabrikamTemplate().TextTransform();  
  
```  
  
## <a name="guidelines-for-all-t4-templates"></a>对于所有 T4 模板的指导原则  
 从文本生成的单独数据收集  
 尽量避免混合使用计算和文本块。 在每个文本模板中，使用第一个\<块 # # 代码&1;> 设置变量并执行复杂计算。 到的模板或第一个结尾的第一个文本块从\<#+ 类功能块 #&1;>，避免长表达式，并避免循环和条件，除非它们包含文本块。 这种做法使模板更轻松地阅读和维护。  
  
 不要使用`.tt`包含文件  
 使用不同的文件扩展名，如`.ttinclude`包含文件。 使用`.tt`仅为你想要的文件处理为运行时或设计时文本模板。 在某些情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]识别`.tt`文件并自动设置其属性以进行处理。  
  
 以固定原型启动每个模板。  
 编写你想要生成，并确保其正确无误的代码或文本的示例。 然后将其扩展名更改为.tt 然后逐步插入通过读取模型修改内容的代码。  
  
 请考虑使用类型化的模型。  
 虽然可以为您的模型创建一个 XML 或数据库架构，但它可能会创建域特定语言 (DSL) 很有用。 DSL 的优点，它生成了一个类来表示架构和属性来表示特性中的每个节点。 这意味着，您可以根据业务模型进行编程。 例如：  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 请考虑对您的模型使用关系图。  
 多个模型是最有效地提供和管理是以文本表，尤其是那些非常大。  
  
 但是，对于某些类型的业务需求，务必要阐明复杂的关系和工作流、 集和关系图是最适合的介质。 关系图的优点是很容易地与用户和其他利益干系人一起讨论。 通过从级别的业务需求模型生成代码，可以使您的代码更具灵活性要求发生更改时。  
  
 您还可以作为一种域特定语言 (DSL) 来设计您自己的关系图的类型。 可以从 UML 和 Dsl 生成代码。 有关详细信息，请参阅[分析和建模体系结构](../modeling/analyze-and-model-your-architecture.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)

