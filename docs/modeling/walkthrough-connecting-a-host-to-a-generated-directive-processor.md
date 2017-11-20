---
title: "演练： 连接到生成的指令处理器的主机 |Microsoft 文档"
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
caps.latest.revision: "47"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 07b1e70775638d88e67280f2f914412ef4271a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>演练：将主机连接至生成的指令处理器
你可以编写您自己处理文本模板的主机。 在演示了基本的自定义主机[演练： 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。 你可以扩展此主机不能添加功能，如生成多个输出文件。  
  
 在本演练中，你将展开自定义宿主，以使它支持调用指令处理器的文本模板。 当你定义的域特定语言时，它会生成*指令处理器*域模型。 指令处理器，使用户更轻松地编写访问的模型，从而减少编写程序集并导入的模板中的指令的需要的模板。  
  
> [!WARNING]
>  本演练基于[演练： 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。 第一次执行该演练。  
  
 本演练包含以下任务：  
  
-   使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]生成基于域模型的指令处理器。  
  
-   连接到生成的指令处理器了自定义文本模板宿主。  
  
-   测试自定义主机与生成的指令处理器。  
  
## <a name="prerequisites"></a>先决条件  
 若要定义 DSL，必须安装以下组件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio 可视化和建模 SDK||  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 此外，你必须在中创建自定义文本模板转换[演练： 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>使用域特定语言工具生成指令处理器  
 在本演练中，你将使用域特定语言设计器向导来创建域特定语言解决方案 DSLMinimalTest。  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>使用域特定语言工具来生成基于域模型的指令处理器  
  
1.  创建域特定语言解决方案具有以下特征：  
  
    -   名称： DSLMinimalTest  
  
    -   解决方案模板： 最小的语言  
  
    -   文件扩展名： 最小值  
  
    -   公司名称： Fabrikam  
  
     有关创建域特定语言解决方案的详细信息，请参阅[如何： 创建域特定语言解决方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。  
  
2.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
    > [!IMPORTANT]
    >  此步骤生成指令处理器，并为其在注册表中添加键。  
  
3.  在“调试”菜单上，单击“启动调试”。  
  
     第二个实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]打开。  
  
4.  在实验性生成、 在**解决方案资源管理器**，双击该文件**sample.min**。  
  
     在设计器中打开该文件。 请注意该模型具有两个元素、 ExampleElement1 和 ExampleElement2 和它们之间的链接。  
  
5.  关闭的第二个实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
6.  保存的解决方案，然后关闭域特定语言设计器。  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>连接到的指令处理器了自定义文本模板宿主  
 生成指令处理器后，连接指令处理器和你在中创建自定义文本模板宿主[演练： 创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)。  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>若要连接到生成的指令处理器了自定义文本模板宿主  
  
1.  打开 CustomHost 解决方案。  
  
2.  在“项目”菜单上，单击“添加引用”。  
  
     **添加引用**对话框将打开带有**.NET**显示的选项卡。  
  
3.  添加以下引用：  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  在 Program.cs 或 Module1.vb 顶部，添加以下代码行：  
  
    ```csharp  
    using Microsoft.Win32;  
    ```  
  
    ```vb  
    Imports Microsoft.Win32  
    ```  
  
5.  定位属性的代码`StandardAssemblyReferences`，并将其替换为以下代码：  
  
    > [!NOTE]
    >  在此步骤中，你将添加对所需的生成你的主机将支持的指令处理器的程序集的引用。  
  
    ```csharp  
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
  
6.  定位该函数的代码`ResolveDirectiveProcessor`，并将其替换为以下代码：  
  
    > [!IMPORTANT]
    >  此代码包含硬编码引用生成的指令处理器你想要连接的名称。 你可以轻松地进行这更多常规，在这种情况下它会查找所有指令处理器的注册表中列并尝试找到匹配项。 在这种情况下，主机会使用任何生成的指令处理器。  
  
    ```csharp  
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
  
7.  上**文件**菜单上，单击**保存所有**。  
  
8.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>测试指令处理器的自定义主机  
 若要测试自定义文本模板宿主，首先必须编写一个调用生成的指令处理器的文本模板。 然后运行自定义宿主，将文本模板的名称传递给它并验证已正确处理指令。  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>创建文本模板测试自定义主机  
  
1.  创建一个文本文件，并将其命名`TestTemplateWithDP.tt`。 可以使用任何文本编辑器，如记事本，以创建文件。  
  
2.  向文本文件中添加以下内容：  
  
    > [!NOTE]
    >  文本模板的编程语言不必与自定义主机名称相匹配。  
  
    ```csharp  
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
  
    ```vb  
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
  
3.  在代码中，替换\<你的路径 > 中第一个过程中创建的设计特定于语言的 Sample.min 文件的路径。  
  
4.  保存并关闭文件。  
  
#### <a name="to-test-the-custom-host"></a>测试自定义主机  
  
1.  打开一个命令提示符窗口。  
  
2.  为自定义宿主键入可执行文件的路径，但暂不要按 Enter。  
  
     例如，键入：  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  而不键入地址，你可以浏览到文件 CustomHost.exe 中**Windows 资源管理器**，，然后将文件拖入命令提示符窗口。  
  
3.  键入一个空格。  
  
4.  键入文本模板文件的路径，然后按 Enter。  
  
     例如，键入：  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  而不键入地址，你可以浏览到文件 TestTemplateWithDP.txt 中**Windows 资源管理器**，，然后将文件拖入命令提示符窗口。  
  
     自定义主机应用程序运行，并启动文本模板转换过程。  
  
5.  在**Windows 资源管理器**，浏览到包含文件 TestTemplateWithDP.txt 的文件夹。  
  
     该文件夹还包含文件 TestTemplateWithDP1.txt。  
  
6.  打开此文件可以查看文本模板转换的结果。  
  
     生成的文本输出的结果显示，且应如下所示：  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [演练：创建自定义文本模板宿主](../modeling/walkthrough-creating-a-custom-text-template-host.md)
