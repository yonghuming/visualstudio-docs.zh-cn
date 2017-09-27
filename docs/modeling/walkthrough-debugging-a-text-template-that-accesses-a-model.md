---
title: "演练： 调试文本模板访问模型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2943b49571077ac1cab87db5ecc4d0f82390273e
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>演练：调试访问模型的文本模板
当你修改或域特定语言解决方案中添加文本模板时时引擎转换模板源代码或在编译生成的代码时, 可能会收到错误。 下面的演练演示的一些操作可以执行操作来调试文本模板。  
  
> [!NOTE]
>  有关文本模板通常情况下，请参阅[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。 有关调试文本模板的详细信息，请参阅[演练： 调试文本模板](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f)。  
  
## <a name="creating-a-domain-specific-language-solution"></a>创建域特定语言解决方案  
 在此过程中，你将创建具有以下特征的域特定语言解决方案：  
  
-   名称： DebuggingTestLanguage  
  
-   解决方案模板： 最小的语言  
  
-   文件扩展名：.ddd  
  
-   公司名称： Fabrikam  
  
 有关创建域特定语言解决方案的详细信息，请参阅[如何： 创建域特定语言解决方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。  
  
## <a name="creating-a-text-template"></a>创建文本模板  
 将文本模板添加到你的解决方案。  
  
#### <a name="to-create-a-text-template"></a>若要创建文本模板  
  
1.  生成解决方案并开始在调试器中运行它。 (在**生成**菜单上，单击**重新生成解决方案**，然后在**调试**菜单上，单击**启动调试**。)Visual Studio 的新实例将打开调试项目。  
  
2.  添加一个名为文本文件`DebugTest.tt`到调试项目。  
  
3.  请确保**自定义工具**DebugTest.tt 属性设置为`TextTemplatingFileGenerator`。  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>从文本模板访问模型的调试指令  
 你可以从语句中的和表达式文本模板访问模型之前，你必须首先调用生成的指令处理器。 调用生成的指令处理器使类成为您的模型中可供文本模板代码作为属性。 有关详细信息，请参阅[从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)。  
  
 在下面的过程中，你将调试不正确的指令名称和不正确的属性名称。  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>若要调试不正确的指令名称  
  
1.  DebugTest.tt 中的代码替换为以下代码：  
  
    > [!NOTE]
    >  该代码包含错误。 若要对其进行调试，正在引入错误。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  在**解决方案资源管理器**，右键单击 DebugTest.tt，，然后单击**运行自定义工具**。  
  
     **错误列表**窗口将显示此错误：  
  
     **名为 DebuggingTestLanguageDirectiveProcessor 处理器不支持名为根本指令。转换将不会运行。**  
  
     在这种情况下，指令调用包含不正确的指令名称。 已指定`modelRoot`原样指令的名称，但正确指令名称`DebuggingTestLanguage`。  
  
3.  双击中的错误**错误列表**跳转到代码的窗口。  
  
4.  若要更正代码，指令名称更改为`DebuggingTestLanguage`。  
  
     更改会突出显示。  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  在**解决方案资源管理器**，右键单击 DebugTest.tt，，然后单击**运行自定义工具**。  
  
     现在系统转换文本模板，并生成相应的输出文件。 你将看不到中的任何错误**错误列表**窗口。  
  
#### <a name="to-debug-an-incorrect-property-name"></a>若要调试的不正确的属性名称  
  
1.  DebugTest.tt 中的代码替换为以下代码：  
  
    > [!NOTE]
    >  该代码包含错误。 若要对其进行调试，正在引入错误。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  在**解决方案资源管理器**，右键单击 DebugTest.tt，，然后单击**运行自定义工具**。  
  
     **错误列表**窗口随即出现并显示以下错误之一：  
  
     (C#)  
  
     **编译转换： Microsoft.VisualStudio.TextTemplating\<GUID >。GeneratedTextTransformation 未包含 ExampleModel 的定义**  
  
     (Visual Basic)  
  
     **编译转换: ExampleModel 不是的成员 Microsoft.VisualStudio.TextTemplating\<GUID >。GeneratedTextTransformation。**  
  
     在这种情况下，文本模板代码包含不正确的属性名称。 已指定`ExampleModel`为属性名称，但正确的属性名称是`LibraryModel`。 你可以查找中的正确的属性名称提供参数，如下面的代码中所示：  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  双击错误列表窗口跳转到代码中的错误。  
  
4.  若要更正代码，属性名称更改为`LibraryModel`中的文本模板代码。  
  
     突出显示所做的更改。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  在**解决方案资源管理器**，右键单击 DebugTest.tt，，然后单击**运行自定义工具**。  
  
     现在系统转换文本模板，并生成相应的输出文件。 你将看不到中的任何错误**错误列表**窗口。
