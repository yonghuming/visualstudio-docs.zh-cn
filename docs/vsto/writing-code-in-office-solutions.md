---
title: "在 Office 解决方案中编写代码"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.RefactoringCancelled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "解决方案 [Visual Studio 中的 Office 开发]，编写代码"
  - "托管代码 [Visual Studio 中的 Office 开发]"
  - "Visual Studio 中的 Office 开发，支持的编程语言"
  - "Office 应用程序 [Visual Studio 中的 Office 开发]，自动化"
  - "Office 应用程序 [Visual Studio 中的 Office 开发]，编写代码"
  - "为 Office 解决方案写代码"
  - "编程 [Visual Studio 中的 Office 开发]，模型"
  - "自动化 [Visual Studio 中的 Office 开发]，托管代码"
  - "应用程序开发 [Visual Studio 中的 Office 开发]，编程模型"
  - "Office 解决方案 [Visual Studio 中的 Office 开发]，编写代码"
  - "自动化 Office 应用程序"
  - "应用程序开发 [Visual Studio 中的 Office 开发]，编写代码"
  - "应用程序开发 [Visual Studio 中的 Office 开发]，自动化"
  - "Office 项目 [Visual Studio 中的 Office 开发]，更改命名空间"
  - "解决方案 [Visual Studio 中的 Office 开发]，编程模型"
  - "编程 [Visual Studio 中的 Office 开发]"
  - "命名空间 [Visual Studio 中的 Office 开发]，在 Office 解决方案中更改"
  - "项目 [Visual Studio 中的 Office 开发]，编写代码"
  - "Office 应用程序 [Visual Studio 中的 Office 开发]，编程模型"
  - "托管代码扩展 [Visual Studio 中的 Office 开发]，编写代码"
ms.assetid: 2d4d8fd0-e881-4829-976f-0d1a9221dec0
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 在 Office 解决方案中编写代码
  编写 Office 项目代码与编写 Visual Studio 中其他类型的代码在某些方面存在不同。 其中许多差异与 Office 对象模型公开给托管代码的方式相关。 其他差异与 Office 项目的设计相关。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 托管代码和 Office 编程  
 使创建集成的 Microsoft Office 解决方案成为可能的关键技术是自动化，它是组件对象模型 \(COM\) 技术的一部分。 自动化使你能够使用代码来创建和控制由任何应用程序、DLL 或支持相应编程接口的 ActiveX 控件公开的软件对象。  
  
### 了解主互操作程序集  
 Microsoft Office 应用程序向自动化公开其大部分功能。 但是，不能直接使用托管代码（如 Visual Basic 或 C\# ）来自动执行 Office 应用程序。 若要使用托管代码来自动执行 Office 应用程序，必须使用 Office 主互操作程序集 \(PIA\)。 主互操作程序集使托管代码可与 Office 应用程序的基于 COM 的对象模型进行交互。  
  
 每个 Microsoft Office 应用程序都有 PIA。 当你在 Visual Studio 中创建 Office 项目时，则对相应 PIA 的引用将自动添加到项目中。 为了自动执行来自项目的其他 Office 应用程序的功能，必须手动添加对相应 PIA 的引用。 有关更多信息，请参见[如何：通过主互操作程序集面向 Office 应用程序](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)。  
  
### 在设计时和运行时使用主互操作程序集  
 必须在开发计算机上的全局程序集缓存中安装并注册 Office PIA 才能执行大多数开发任务。 有关详细信息，请参阅[将计算机配置为开发 Office 解决方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。  
  
 若要运行面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的 Office 解决方案，无需在最终用户计算机上安装 Office PIA。 有关详细信息，请参阅[设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)。  
  
### 在主互操作程序集中使用类型  
 Office PIA 包含类型组合，该类型组合公开 Office 应用程序和不应直接在代码中使用的其他基础结构类型的对象模型。 有关 Office PIA 中的类型的概述，请参阅 [Overview of Classes and Interfaces in the Office Primary Interop Assemblies](http://msdn.microsoft.com/zh-cn/da92dc3c-8209-44de-8095-a843659368d5)。  
  
 由于 Office PIA 中的类型对应于基于 COM 的对象模型中的类型，因此使用这些类型的方式通常不同于其他托管类型。 例如，调用在 Office 主互操作程序集中具有可选参数的方法的方式取决于你正在项目中使用的编程语言。 有关更多信息，请参见下列主题：  
  
-   [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)。  
  
-   [Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)。  
  
## Office 项目的编程模型  
 所有 Office 项目都包括一个或多个为你的代码提供入口点的生成类。 这些类还提供对主机应用程序的对象模型的访问以及对操作窗格和自定义任务窗格等功能的访问。  
  
### 了解生成类  
 在 Excel 和 Word 的文档级项目中，生成的类类似于应用程序对象模型中的顶级对象。 例如，Word 文档项目中生成的 `ThisDocument` 类与 Word 对象模型中的 <xref:Microsoft.Office.Interop.Word.Document> 类提供相同的成员。 有关文档级项目中的生成类的详细信息，请参阅[对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)。  
  
 VSTO 外接程序项目提供一个名为 `ThisAddIn` 的生成类。 此类与主机应用程序的对象模型中的类不同。 此类表示 VSTO 外接程序本身，并且它提供可用于访问主机应用程序的对象模型和访问 VSTO 外接程序提供的其他功能的成员。 有关更多信息，请参见[VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。  
  
 Office 项目中的所有生成类均包括 `Startup` 和 `Shutdown` 事件处理程序。 若要开始编写代码，通常将代码添加到这些事件处理程序中。 若要初始化 VSTO 外接程序，可以将代码添加到 `Startup` 事件处理程序中。 若要清理 VSTO 外接程序使用的资源，可以将代码添加到 `Shutdown` 事件处理程序中。 有关详细信息，请参阅[Office 项目中的事件](../vsto/events-in-office-projects.md)。  
  
### 在运行时访问生成类  
 加载 Office 解决方案后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 将实例化项目中的每个生成类。 可以通过使用 `Globals` 类从项目中的任何代码访问这些对象。 例如，可以使用 `Globals` 类来从 VSTO 外接程序中功能区按钮的事件处理程序调用 `ThisAddIn` 类中的代码。  
  
 有关详细信息，请参阅[对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)。  
  
### Office 解决方案中的命名空间注意事项  
 创建项目后，不能更改 Office 项目的*“默认命名空间”*（或 Visual Basic 中的*“根命名空间”*）。 创建项目后，默认命名空间将始终与你指定的项目名匹配。 如果你重命名项目，将不会更改默认命名空间。 有关项目中的默认命名空间的详细信息，请参阅[“项目设计器”-&#62;“应用程序”页 &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) 和[“项目设计器”, “应用程序”页 &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
### 更改 C\# 项目中的主机项类的命名空间  
 主机项类（例如，`ThisAddIn`、`ThisWorkbook` 或 `ThisDocument` 类）在 Visual C\# Office 项目中具有自己的命名空间。 默认情况下，在创建项目后，项目中的主机项的命名空间与你指定的项目名相匹配。  
  
 若要更改 Visual C\# Office 项目中的主机项的命名空间，请使用**“主机项的命名空间”**属性。 有关详细信息，请参阅[Office 项目中的属性](../vsto/properties-in-office-projects.md)。  
  
## Office 项目中受支持的编程语言  
 Visual Studio 中的 Office 项目模板仅支持 Visual Basic 和 Visual C\# 编程语言。 因此，这些项目模板只能在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的**“新建项目”**对话框的**“Visual Basic”**和**“Visual C\#”**节点下找到。 有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
## 语言选择和 Office 编程  
 Microsoft Office 和 Visual Basic for Applications \(VBA\) 被开发为协同工作以优化应用程序自定义项的工作流。 Visual Basic 已继承其中一些开发。 例如，Visual Basic 支持可选的参数，这意味着你在调用 Microsoft Office 主互操作程序集中的一些方法时编写的代码比使用 Visual C\# 时少。  
  
## 使用 Visual Basic 与 Visual C\# 在 Office 解决方案中编程  
 你可以通过使用 Visual Basic 或 Visual C\# 创建 Office 解决方案。 由于 Microsoft Office 对象模型被设计为与 Microsoft Visual Basic for Applications \(VBA\) 一起使用，因此 Visual Basic 开发人员可以轻松使用由 Microsoft Office 应用程序公开的对象。 Visual C\# 开发人员可以使用与 Visual Basic 开发人员相同的大多数功能，但在某些情况下，他们必须编写附加代码才能使用 Office 对象模型。 Office 开发中的基本编程功能与在 Visual Basic 和 C\# 中编写的托管代码之间也有一些差异。  
  
## Visual Basic 与 Visual C\# 之间的主要差异  
 下表显示了 Office 开发中 Visual Basic 与 Visual C\# 之间的主要差异。  
  
|功能|描述|Visual Basic 支持|Visual C\# 支持|  
|--------|--------|---------------------|-------------------|  
|可选参数|许多 Microsoft Office 方法具有调用该方法时不需要的参数。 如果没有为参数传递任何值，则使用默认值。|Visual Basic 支持可选参数。|Visual C\# 在大多数情况下支持可选参数。 有关详细信息，请参阅[Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)。|  
|按引用传递参数|大多数 Microsoft Office 主互操作程序集中的可选参数可以按值传递。 但是，在某些主互操作程序集中，接受引用类型的可选参数必须按引用传递。<br /><br /> 有关值和引用类型参数的详细信息，请参阅[通过值和通过引用传递参数 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)（适用于 Visual Basic）和[传递参数（C&#35; 编程指南）](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)。|按引用传递参数不需要完成任何额外工作。 Visual Basic 编译器在必要时会自动按引用传递参数。|大多数情况下，Visual C\# 编译器在必要时会自动按引用传递参数。 有关详细信息，请参阅[Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)。|  
|参数化属性|某些属性接受参数，并充当只读函数。|Visual Basic 支持接受参数的属性。|Visual C\# 支持接受参数的属性。|  
|后期绑定|后期绑定涉及在运行时确定对象的属性，而不是在设计时将变量强制转换为对象类型。|当 **Option Strict** 处于关闭状态时，Visual Basic 执行后期绑定。 当 **Option Strict** 处于启用状态时，必须显式转换对象并使用 <xref:System.Reflection> 命名空间中的类型访问后期绑定成员。 有关更多信息，请参见[Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)。|Visual C\# 在面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的项目中执行后期绑定。 有关详细信息，请参阅[Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)。|  
  
## Office 开发代码与托管代码之间的主要差异  
 下表显示了 Office 开发代码与在 Visual Basic 或 Visual C\# 中编写的托管代码之间的主要差异。  
  
|功能|描述|Visual Basic 和 Visual C\# 支持|  
|--------|--------|----------------------------------|  
|数组索引|Microsoft Office 应用程序中集合的数组下限从 1 开始。 Visual Basic 和 Visual C\# 使用基于 0 的数组。 有关详细信息，请参阅 [数组（C&#35; 编程指南）](/dotnet/csharp/programming-guide/arrays/index) 和 [Visual Basic 中的数组](/dotnet/visual-basic/programming-guide/language-features/arrays/index)。|若要访问 Microsoft Office 应用程序对象模型中某个集合的第一项，请使用索引 1，而不是 0。|  
  
## 请参阅  
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 项目中的事件](../vsto/events-in-office-projects.md)   
 [如何：通过主互操作程序集面向 Office 应用程序](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)   
 [合作开发 Office 解决方案](../vsto/collaborative-development-of-office-solutions.md)  
  
  