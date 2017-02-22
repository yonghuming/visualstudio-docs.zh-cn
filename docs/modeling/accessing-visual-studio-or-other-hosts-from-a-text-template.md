---
title: "从文本模板访问 Visual Studio 或其他主机 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
caps.handback.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 从文本模板访问 Visual Studio 或其他主机
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在文本模板中，可以使用执行模板的主机（例如 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]）公开的方法和属性。  
  
 这适用于常规文本模板，而不是预处理过的文本模板。  
  
## 获取对主机的访问  
 在 `template` 指令中设置 `hostspecific="true"`。  这样可以使用 `this.Host`，其类型为 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>。  例如，此类型具有您可以用于解析文件名并记录错误的成员。  
  
### 解析文件名  
 若要查找文件相对于文本模板的完整路径，请使用 this.Host.ResolvePath\(\)。  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
### 显示错误消息  
 此示例会在您转换模板时记录消息。  如果主机是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，则将它们添加到错误窗口。  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.CodeDom.Compiler" #>  
<#  
  string message = "test message";  
  this.Host.LogErrors(new CompilerErrorCollection()   
    { new CompilerError(  
       this.Host.TemplateFile, // Identify the source of the error.  
       0, 0, "0",   // Line, column, error ID.  
       message) }); // Message displayed in error window.  
#>  
  
```  
  
## 使用 Visual Studio API  
 如果您要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中执行文本模板，则可以使用 `this.Host` 访问 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供的服务以及加载的任何包或扩展。  
  
 设置 hostspecific\="true" 并将 `this.Host` 转换为 <xref:System.IServiceProvider>。  
  
 此示例获取 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API <xref:EnvDTE.DTE> 作为服务：  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#   
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
```  
  
## 使用 hostSpecific 模板继承  
 指定`hostspecific="trueFromBase"`如果还使用`inherits`属性中，如果您指定的模板从继承和`hostspecific="true"`。  这样可以避免编译器警告的效果的属性`Host`两次声明。