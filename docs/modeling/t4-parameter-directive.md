---
title: "T4 参数指令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# T4 参数指令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 文本模板中，`parameter` 指令声明模板代码中从自外部上下文传入的值初始化的属性。  如果编写调用文本转换的代码，则可以设置这些值。  
  
## 使用参数指令  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 `parameter` 指令声明模板代码中从自外部上下文传入的值初始化的属性。  如果编写调用文本转换的代码，则可以设置这些值。  这些值既可以在 `Session` 字典中传递，也可以在 <xref:System.Runtime.Remoting.Messaging.CallContext> 中传递。  
  
 可以声明任何远程类型的参数。  也就是说，类型必须使用 <xref:System.SerializableAttribute> 进行声明，或者必须从 <xref:System.MarshalByRefObject> 派生。  这样可以将参数值传递到在其中处理模板的 AppDomain 中。  
  
 例如，可以使用以下内容编写文本模板：  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## 将参数值传递到模板  
 如果要编写诸如菜单命令或事件处理程序等的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展，则可以使用文本模板化服务来处理模板：  
  
```c#  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## 在调用上下文中传递值  
 或者，您可以在 <xref:System.Runtime.Remoting.Messaging.CallContext> 中作为逻辑数据传递值。  
  
 以下示例使用这两种方法来传递值：  
  
```c#  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## 将值传递给运行时（预处理过的）文本模板  
 通常没有必要将 `<#@parameter#>` 指令与运行时（预处理过的）文本模板配合使用。  相反，可以为生成的代码（通过它可以传递参数值）定义其他构造函数或可设置属性。  有关更多信息，请参见[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
 然而，如果要在运行时模板中使用 `<#@parameter>`，则可以使用会话字典将值传递给该参数。  举例来说，假设您已经创建了作为预处理过的模板（名为 `PreTextTemplate1`）的文件。  可以使用以下代码在您的程序中调用该模板。  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## 从 TextTemplate.exe 获得参数  
  
> [!IMPORTANT]
>  `parameter` 指令不检索在 `TextTransform.exe` 实用工具的 `–a` 参数中设置的值。  若要获得这些值，请在 `template` 指令中设置 `hostSpecific="true"`，并使用 `this.Host.ResolveParameterValue("","","argName")`。