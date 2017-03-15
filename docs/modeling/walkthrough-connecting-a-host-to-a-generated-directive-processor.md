---
title: "演练︰ 连接到生成的指令处理器的主机 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 47
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 3cdbd2adb7b956849e5582e8a5b1ca80a6f5166d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>演练：将主机连接至生成的指令处理器
您可以编写您自己处理文本模板的主机。 基本的自定义主机中进行了演示[演练︰ 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。 您可以扩展此主机不能添加功能，如生成多个输出文件。  
  
 本演练中，展开您的自定义主机，以便它支持调用指令处理器的文本模板。 在定义特定于域的语言，它将生成*指令处理器*域模型。 指令处理器，使用户更轻松地编写访问模型，减少了需要编写程序集并导入的模板中的指令的模板。  
  
> [!WARNING]
>  本演练基于[演练︰ 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。 第一次执行该演练。  
  
 本演练包含以下任务：  
  
-   使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]来生成基于域模型的指令处理器。  
  
-   自定义文本模板将主机连接到生成的指令处理器。  
  
-   测试自定义宿主与生成的指令处理器。  
  
## <a name="prerequisites"></a>先决条件  
 若要定义 DSL，必须安装以下组件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio 可视化和建模 SDK||  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 此外，您必须具有在中创建自定义文本模板转换[演练︰ 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>使用域特定语言工具来生成指令处理器  
 在本演练中，使用域特定语言设计器向导来创建域特定语言解决方案 DSLMinimalTest。  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>若要使用域特定语言工具来生成基于域模型的指令处理器  
  
1.  创建域特定语言解决方案具有以下特征︰  
  
    -   名称︰ DSLMinimalTest  
  
    -   解决方案模板︰ 最小语言  
  
    -   文件扩展名︰ 最小值  
  
    -   公司名称︰ Fabrikam  
  
     有关创建域特定语言解决方案的详细信息，请参阅[如何︰ 创建域特定语言解决方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。  
  
2.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
    > [!IMPORTANT]
    >  此步骤中生成指令处理器，并为其在注册表中添加键。  
  
3.  在**调试**菜单上，单击**开始调试**。  
  
     第二个实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]随即打开。  
  
4.  在实验性生成中**解决方案资源管理器**，双击该文件**sample.min**。  
  
     在设计器中打开该文件。 请注意该模型具有两个元素、 ExampleElement1 和 ExampleElement2 和它们之间的链接。  
  
5.  关闭第二个实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
6.  保存的解决方案，然后关闭域特定语言设计器。  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>自定义文本模板将主机连接到的指令处理器  
 生成指令处理器后，连接指令处理器和你在中创建自定义文本模板宿主[演练︰ 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>若要连接到生成的指令处理器了自定义文本模板宿主  
  
1.  打开 CustomHost 解决方案。  
  
2.  在**项目**菜单上，单击**添加引用**。  
  
     **添加引用**对话框将打开带有**.NET**显示选项卡。  
  
3.  添加以下引用︰  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  在 Program.cs 或 Module1.vb 顶部，添加以下代码行︰  
  
    ```c#  
    using Microsoft.Win32;  
    ```  
  
    ```vb#  
    Imports Microsoft.Win32  
    ```  
  
5.  找到该属性的代码`StandardAssemblyReferences`，并将其替换为以下代码︰  
  
    > [!NOTE]
    >  在此步骤中，添加对所需的生成将支持您的主机的指令处理器的程序集的引用。  
  
    ```c#  
    //the host can provide standard assembly references  
    //the engine will use these references when compiling and  
    //executing the generated transformation class  
    //--------------------------------------------------------------  
    public IList<string> StandardAssemblyReferences  
    {  
        get  
        {  
            return new string[]  
            {  
                //if this host searches standard paths and the GAC  
                //we can specify the assembly name like this:  
                //"System"  
                //since this host only resolves assemblies from the   
                //fully qualified path and name of the assembly  
                //this is a quick way to get the code to give us the  
                //fully qualified path and name of the System assembly  
                //---------------------------------------------------------  
                typeof(System.Uri).Assembly.Location,  
                            typeof(System.Uri).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location  
  
            };  
        }  
    }  
    ```  
  
6.  找到该函数的代码`ResolveDirectiveProcessor`，并将其替换为以下代码︰  
  
    > [!IMPORTANT]
    >  此代码包含硬编码引用生成的指令处理器你想要连接的名称。 你可以轻松地进行这更为通用，在这种情况下它会查找所有指令处理器列在注册表中并将尝试查找匹配项。 在这种情况下，宿主将工作与任何生成的指令处理器。  
  
    ```c#  
    //the engine calls this method based on the directives the user has   
            //specified it in the text template  
            //this method can be called 0, 1, or more times  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //check the processor name, and if it is the name of the processor the   
                //host wants to support, return the type of the processor  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)  
                {  
                    try  
                    {  
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";  
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))  
                        {  
                            if (specificKey != null)  
                            {  
                                List<string> names = new List<String>(specificKey.GetValueNames());  
                                string classValue = specificKey.GetValue("Class") as string;  
                                if (!string.IsNullOrEmpty(classValue))  
                                {  
                                    string loadValue = string.Empty;  
                                    System.Reflection.Assembly processorAssembly = null;  
                                    if (names.Contains("Assembly"))  
                                    {  
                                        loadValue = specificKey.GetValue("Assembly") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //the assembly must be installed in the GAC  
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);  
                                        }  
                                    }  
                                    else if (names.Contains("CodeBase"))  
                                    {  
                                        loadValue = specificKey.GetValue("CodeBase") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //loading local assembly  
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);  
                                        }  
                                    }  
                                    if (processorAssembly == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    Type processorType = processorAssembly.GetType(classValue);  
                                    if (processorType == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    return processorType;  
                                }  
                            }  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        //if the directive processor can not be found, throw an error  
                        throw new Exception("Directive Processor not found");  
                    }  
                }  
  
                //if the directive processor is not one this host wants to support  
                throw new Exception("Directive Processor not supported");  
            }  
    ```  
  
7.  在**文件**菜单上，单击**全部保存**。  
  
8.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>测试自定义宿主与指令处理器  
 若要测试自定义文本模板宿主，首先必须编写一个调用生成的指令处理器的文本模板。 然后运行自定义宿主，传递给该文本模板的名称并验证已正确处理指令。  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>创建文本模板测试自定义主机  
  
1.  创建一个文本文件，并将其命名`TestTemplateWithDP.tt`。 可以使用任何文本编辑器，如记事本，以创建文件。  
  
2.  向文本文件中添加以下内容：  
  
    > [!NOTE]
    >  文本模板的编程语言不需要自定义宿主的相匹配。  
  
    ```c#  
    Text Template Host Test  
  
    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
    <# //this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
    <# //uncomment this line to test that the host allows the engine to set the extension #>  
    <# //@ output extension=".htm" #>  
  
    <# //uncomment this line if you want to see the generated transformation class #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
    <# //this code uses the results of the examplemodel directive #>  
    <#  
        foreach ( ExampleElement box in this.ExampleModel.Elements )   
        {   
            WriteLine("Box: {0}", box.Name);  
  
            foreach (ExampleElement linkedTo in box.Targets)  
            {  
                WriteLine("Linked to: {0}", linkedTo.Name);  
            }  
  
            foreach (ExampleElement linkedFrom in box.Sources)  
            {  
                WriteLine("Linked from: {0}", linkedFrom.Name);  
            }  
  
            WriteLine("");  
        }   
    #>  
    ```  
  
    ```vb#  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
  
    <# 'this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to see the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# 'this code uses the results of the examplemodel directive #>  
  
    <#      
       For Each box as ExampleElement In Me.ExampleModel.Elements   
  
           WriteLine("Box: {0}", box.Name)  
  
            For Each LinkedTo as ExampleElement In box.Targets  
                WriteLine("Linked to: {0}", LinkedTo.Name)  
            Next  
  
            For Each LinkedFrom as ExampleElement In box.Sources  
                WriteLine("Linked from: {0}", LinkedFrom.Name)  
            Next  
  
            WriteLine("")  
  
       Next   
    #>  
    ```  
  
3.  在代码中，替换\<您路径&1;> 中第一个过程中创建的设计特定于语言的 Sample.min 文件的路径。  
  
4.  保存并关闭该文件。  
  
#### <a name="to-test-the-custom-host"></a>测试自定义主机  
  
1.  打开一个命令提示符窗口。  
  
2.  为自定义宿主键入可执行文件的路径，但暂不要按 Enter。  
  
     例如，键入：  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  而不键入地址，您可以浏览到文件 CustomHost.exe 中**Windows 资源管理器**，然后将该文件拖入命令提示符窗口。  
  
3.  键入一个空格。  
  
4.  键入文本模板文件的路径，然后按 Enter。  
  
     例如，键入：  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  而不键入地址，您可以浏览到文件 TestTemplateWithDP.txt 中**Windows 资源管理器**，然后将该文件拖入命令提示符窗口。  
  
     自定义宿主应用程序运行，并将启动文本模板转换过程。  
  
5.  在**Windows 资源管理器**，浏览到包含文件 TestTemplateWithDP.txt 的文件夹。  
  
     该文件夹还包含文件 TestTemplateWithDP1.txt。  
  
6.  打开此文件可以查看文本模板转换的结果。  
  
     生成的文本输出的结果显示，并应如下所示︰  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [演练：创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)

