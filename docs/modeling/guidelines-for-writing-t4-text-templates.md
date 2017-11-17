---
title: "T4 文本模板编写准则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: "9"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 6baa3086d1a81ce433a077ab1ed0dff4cb152308
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="guidelines-for-writing-t4-text-templates"></a>T4 文本模板编写准则
以下常规准则可能有用，如果正在生成程序代码或中的其他应用程序资源[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它们不被固定的规则。  
  
## <a name="guidelines-for-design-time-t4-templates"></a>设计时 T4 模板的准则  
 设计时 T4 模板是模板，在其中生成代码你[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在设计时的项目。 有关详细信息，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 生成应用程序的变量的部分。  
 代码生成是应用的最适用于在项目进行期间可能会更改或将更改应用程序的不同版本之间程序的这些方面的问题。 这些变量方面分开更固定的方面，以便你可以更轻松地确定什么具有要生成。 例如，如果你的应用程序提供了网站，则独立标准的页面服务函数从定义从一页之间的导航路径的逻辑。  
  
 对一个或多个源模型中的变量部分进行编码。  
 模型是文件或每个模板读取它以获取要生成的代码的变量部分的特定值的数据库。 模型可以是数据库、 设计、 关系图或域特定语言的 XML 文件。 通常情况下，一个模型用于生成中的文件多[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目。 每个文件是从单独的模板生成的。  
  
 项目中，可以使用多个模型。 例如，你可以定义 Web 页和页的布局的单独模型之间的导航模型。  
  
 应使模型关注上用户的需求和词汇、 不关注您的实现。  
 例如，在网站应用程序中，你希望模型来指代网页和超链接。  
  
 理想情况下，选择一种形式的演示文稿，其中适合模型表示的信息的类型。 例如，通过网站的导航路径的模型可能框和箭头的图表。  
  
 测试生成的代码。  
 使用手动或自动测试来验证生成的代码按用户所需的方式工作。 避免从同一模型从其生成的代码生成测试。  
  
 在某些情况下，可以直接在模型上执行常规的测试。 例如，你可以编写测试，以确保从任何其他导航可访问网站中的每一页。  
  
 允许自定义代码： 生成分部类。  
 允许你手动编写此外到生成的代码的代码。 很少要能够应对所有可能的变体可能会产生的代码生成架构。 因此，你应会将添加到或重写某些生成的代码。 生成的材料所在.NET 语言如[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，两种策略是特别有用：  
  
-   生成的类应为部分。 这样，您将内容添加到生成的代码。  
  
-   应在对，继承自另一个中生成类。 所有生成的方法和属性，应包含基类和派生的类应包含仅的构造函数。 这使手工编写代码以重写任何生成的方法。  
  
 在诸如 XML 等其他生成语言，使用`<#@include#>`指令即可使手工编写和生成内容的简单组合。 在更复杂的情况下，你可能必须编写后续处理步骤将生成的文件与手工编写的任何文件组合在一起。  
  
 将通用材料移动到包含文件或运行时模板  
 若要避免重复类似的文本块和多个模板中的代码，使用`<#@ include #>`指令。 有关详细信息，请参阅[T4 包含指令](../modeling/t4-include-directive.md)。  
  
 你可以还生成一个单独的项目中的运行时文本模板，并从设计时模板然后调用它们。 若要执行此操作，使用`<#@ assembly #>`指令访问单独的项目。 有关示例，请参阅["继承在文本中的模板"Gareth Jones 博客](http://go.microsoft.com/fwlink/?LinkId=208373)。  
  
 请考虑将较大的代码块移动到单独的程序集。  
 如果你有大型代码块和类功能块，它可能会将此代码的某些移动到在一个单独的项目中编译的方法很有用。 你可以使用`<#@ assembly #>`指令访问在模板中的代码。 有关详细信息，请参阅[T4 程序集指令](../modeling/t4-assembly-directive.md)。  
  
 可以将方法放在模板可以继承一个抽象类。 此抽象类必须继承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>。 有关详细信息，请参阅[T4 模板指令](../modeling/t4-template-directive.md)。  
  
 生成代码，不是配置文件  
 编写一个变量的应用程序的一种方法是编写接受配置文件的通用程序代码。 以这种方式编写的应用程序非常灵活，和业务需求变化，而无需重新生成应用程序时将其重新配置。 但是，此方法的缺点是应用程序将执行效果不如更具体的应用程序。 此外，其程序代码将更难读取和维护，部分原因它必须始终能够处理大多数泛型类型。  
  
 与此相反，其变量部分会在编译之前生成的应用程序可以为强类型。 这样，便可以更轻松且更可靠地编写手工编写的代码并将其与生成集成部件的软件。  
  
 若要获取代码生成的完全优势，尝试生成程序代码而不是配置文件。  
  
 使用生成的代码的文件夹  
 将模板和生成的文件放在名为的项目文件夹**生成的代码**若要让其清除，这不应直接编辑的文件。 如果你创建自定义代码以重写或将添加到生成的类，将这些类放在名为的文件夹**自定义代码**。 典型的项目的结构如下所示：  
  
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
 你可以使用继承共享方法和 T4 文本模板之间的文本块。 有关详细信息，请参阅[T4 模板指令](../modeling/t4-template-directive.md)。  
  
 你还可以使用包含有运行时模板的文件。  
  
 将较大的代码体移动到分部类。  
 每个运行时模板生成一个具有同名的模板的分部类定义。 你可以编写包含同一个类的另一个分部定义的代码文件。 你可以向这种方式中的类添加方法、 字段和构造函数。 可以从模板中的代码块调用这些成员。  
  
 执行此操作的一个优点是代码会更易于编写，因为将使用 IntelliSense。 此外，你可以实现更好的隔离演示文稿与基础逻辑之间。  
  
 例如，在**MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 在**MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 允许自定义代码： 提供扩展点，  
 请考虑生成中的虚方法\<#+ 类功能块 #>。 这允许在无需修改的多种上下文中使用的单个模板。 而不是修改的模板，您可以构造一个派生的类，该类提供的最小的其他逻辑。 派生的类可以是常规的代码，也可以是运行时模板。  
  
 例如，在 MyStandardRunTimeTemplate.tt:  
  
```  
This page is copyright <#= CompanyName() #>.  
<#+ protected virtual string CompanyName() { return ""; } #>  
```  
  
 在应用程序代码中：  
  
```  
class FabrikamTemplate : MyStandardRunTimeTemplate  
{  
  protected override string CompanyName() { return "Fabrikam"; }  
}  
...  
  string PageToDisplay = new FabrikamTemplate().TextTransform();  
  
```  
  
## <a name="guidelines-for-all-t4-templates"></a>对于所有 T4 模板的准则  
 从文本生成的单独数据收集  
 尽量避免混合计算和文本块。 在每个文本模板，使用第一个\<块 # # 代码 > 若要设置变量和执行复杂计算。 从第一个文本块到的模板或第一个末尾\<#+ 类功能块 #>、 避免长表达式，并避免循环和条件语句，除非其包含文本块。 这种做法使模板更易于读取和维护。  
  
 不要使用`.tt`包含文件  
 使用不同的文件扩展名，如`.ttinclude`包含文件。 使用`.tt`仅为你想要的文件处理为运行时或设计时文本模板。 在某些情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]识别`.tt`文件并自动设置其属性以进行处理。  
  
 开始为固定的原型的每个模板。  
 编写你想要生成，并确保其正确无误的代码或文本的示例。 然后将其扩展名更改为.tt 然后逐步插入通过读取模型修改内容的代码。  
  
 请考虑使用类型化的模型。  
 虽然你可以为您的模型创建的 XML 或数据库的架构，它可能会创建域特定语言 (DSL) 很有用。 DSL 的优点它生成一个类来表示架构和属性来表示特性中的每个节点。 这意味着，您可以根据业务模型进行编程。 例如：  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 请考虑使用您的模型关系图。  
 多个模型是最有效地提供，并只需作为文本表格管理，尤其是如果它们是非常大。  
  
 但是，对于某些类型的业务要求，务必要阐明复杂的关系和工作流，集和关系图是最适合的介质。 关系图的一个优点是很容易地与用户和其他利益干系人讨论。 通过从级别的业务要求模型中生成代码，可以使你的代码更灵活在需求更改时。  
  
 你还可以为域特定语言 (DSL) 来设计你自己的关系图的类型。 可以从 UML 和 Dsl 生成代码。 有关详细信息，请参阅[分析和建模体系结构](../modeling/analyze-and-model-your-architecture.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)
