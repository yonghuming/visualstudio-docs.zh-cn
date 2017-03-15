---
title: "在 VS 扩展中调用文本转换 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 5
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
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 0120e0adfed2c27ebd17d446f2f0e5c808acff92
ms.lasthandoff: 02/22/2017

---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>在 VS 扩展中调用文本转换
如果您正在编写 Visual Studio 扩展，如菜单命令或[域特定语言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)，可以使用文本模板化服务转换文本模板。 获取<xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating>服务并将其转换为<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>。</xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating> </xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating>  
  
## <a name="getting-the-text-templating-service"></a>获取文本模板化服务  
  
```c#  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
  
// Process a text template:  
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));  
  
```  
  
## <a name="passing-parameters-to-the-template"></a>将参数传递给模板  
 可以将参数传递给模板。 在模板内，可以使用 `<#@parameter#>` 指令获取参数值。  
  
 对于参数类型，必须使用可序列化的或可封送的类型。 也就是说，必须使用声明类型<xref:System.SerializableAttribute>，或者它必须派生自<xref:System.MarshalByRefObject>。</xref:System.MarshalByRefObject> </xref:System.SerializableAttribute> 此限制是必要的，因为文本模板在单独的 AppDomain 中执行。 所有内置类型，如**System.String**和**System.Int32**是可序列化。  
  
 若要传递参数值，调用代码可以将值放在`Session`字典中，或在<xref:System.Runtime.Remoting.Messaging.CallContext>.</xref:System.Runtime.Remoting.Messaging.CallContext>  
  
 以下示例使用这两种方法来转换一个简短的测试模板：  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte;   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;  
  
// Create a Session in which to pass parameters:  
sessionHost.Session = sessionHost.CreateSession();  
sessionHost.Session["parameter1"] = "Hello";  
sessionHost.Session["parameter2"] = DateTime.Now;  
  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);  
  
// Process a text template:  
string result = t4.ProcessTemplate("",  
   // This is the test template:  
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"  
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"  
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"  
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");  
  
// This test code yields a result similar to the following line:  
//     Test: Hello    07/06/2010 12:37:45    42  
  
```  
  
## <a name="error-reporting-and-the-output-directive"></a>错误报告和输出指令  
 处理过程中出现的任何错误都将显示在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 错误窗口中。 此外，您可以获得错误通知通过指定实现<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>。</xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>的回调  
  
 如果要将结果字符串写入文件，你可能需要知道模板的 `<#@output#>` 指令中指定的文件扩展名和编码。 此信息也将传递给你的回调。 有关详细信息，请参阅[T4 输出指令](../modeling/t4-output-directive.md)。  
  
```c#  
void ProcessMyTemplate(string MyTemplateFile)  
{  
  string templateContent = File.ReadAllText(MyTemplateFile);  
  T4Callback cb = new T4Callback();  
  // Process a text template:  
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);  
  // If there was an output directive in the MyTemplateFile,  
  // then cb.SetFileExtension() will have been called.  
  // Determine the output file name:  
  string resultFileName =   
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),   
        Path.GetFileNameWithoutExtension(MyTemplateFile))   
      + cb.fileExtension;  
  // Write the processed output to file:  
  File.WriteAllText(resultFileName, result, cb.outputEncoding);  
  // Append any error messages:  
  if (cb.errorMessages.Count > 0)  
  {  
    File.AppendAllLines(resultFileName, cb.errorMessages);  
  }  
}  
  
class T4Callback : ITextTemplatingCallback  
{  
  public List<string> errorMessages = new List<string>();  
  public string fileExtension = ".txt";  
  public Encoding outputEncoding = Encoding.UTF8;  
  
  public void ErrorCallback(bool warning, string message, int line, int column)  
  { errorMessages.Add(message); }  
  
  public void SetFileExtension(string extension)  
  { fileExtension = extension; }  
  
  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)  
  { outputEncoding = encoding; }  
}  
  
```  
  
 可以通过类似于下面的模板文件测试代码：  
  
```  
<#@output extension=".htm" encoding="ASCII"#>  
<# int unused;  // Compiler warning "unused variable"  
#>  
Sample text.  
```  
  
 编辑器警告将显示在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 错误窗口中，还将生成对 `ErrorCallback` 的调用。  
  
## <a name="reference-parameters"></a>引用参数  
 可以将值从文本模板传出传递通过使用从<xref:System.MarshalByRefObject>。</xref:System.MarshalByRefObject>派生的参数类  
  
## <a name="related-topics"></a>相关主题  
 若要从预处理过的文本模板生成文本，请执行以下操作：  
 调用已生成类的 `TransformText()` 方法。 有关详细信息，请参阅[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
 若要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展外生成文本，请执行以下操作：  
 定义一个自定义宿主。 有关详细信息，请参阅[通过使用自定义宿主处理文本模板](../modeling/processing-text-templates-by-using-a-custom-host.md)。  
  
 若要生成可以稍后编译并执行的源代码，请执行以下操作：  
 调用`t4.PreprocessTemplate()` <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>。</xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>方法

