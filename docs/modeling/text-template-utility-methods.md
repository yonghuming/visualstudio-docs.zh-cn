---
title: "文本模板实用工具方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, 实用程序方法"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
caps.handback.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 文本模板实用工具方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 文本模板中编写代码时，有几种方法始终可用。  这些方法是在 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 中定义的。  
  
> [!TIP]
>  您还可以在常规（未预处理的）文本模板中使用由宿主环境提供的其他方法和服务。  例如，可以解析文件路径、记录错误以及获得由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和任何已加载包所提供的服务。  有关更多信息，请参见[Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/zh-cn/0556f20c-fef4-41a9-9597-53afab4ab9e4)。  
  
## 写入方法  
 可以使用 `Write()` 和 `WriteLine()` 方法在标准代码块内追加文本，而不必使用表达式代码块。  下面两个代码块在功能上是等效的。  
  
##### 包含表达式块的代码块  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### 使用 WriteLine\(\) 的代码块  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 不通过嵌套控制结构在冗长的代码块中使用表达式块，而是使用这些实用工具方法之一，是非常有用的。  
  
 `Write()` 和 `WriteLine()` 方法有两个重载，其中一个重载接受单个字符串参数，另一个重载接受一个复合格式字符串以及将包含在字符串中的对象数组（与 `Console.WriteLine()` 方法类似）。  下面两种 `WriteLine()` 用法在功能上是等效的：  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## 缩进方法  
 可以使用缩进方法设置文本模板输出的格式。  <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 类具有一个 `CurrentIndent` 字符串属性，该属性显示文本模板中的当前缩进，该类还具有一个 `indentLengths` 字段，该字段是已添加的缩进的列表。  可以使用 `PushIndent()`  方法增加缩进，也可以使用 `PopIndent()` 方法减少缩进。  如果要删除所有缩进，请使用 `ClearIndent()` 方法。  下面的代码块演示这些方法的用法：  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 此代码块产生以下输出：  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## 错误和警告方法  
 可以使用错误和警告实用工具方法向 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 错误列表添加消息。  例如，下面的代码向错误列表添加一条错误消息。  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## 访问宿主和服务提供程序  
 使用 `this.Host` 属性可以访问由执行模板的宿主公开的属性。  若要使用 `this.Host`，必须在 `<@template#>` 指令中设置 `hostspecific` 特性：  
  
 `<#@template ...  hostspecific="true" #>`  
  
 `this.Host` 的类型取决于执行模板的宿主的类型。  在运行于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的模板中，可以将 `this.Host` 强制转换为 `IServiceProvider`，以获取对服务（如 IDE）的访问。  例如：  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## 使用其他实用工具方法集  
 在文本生成过程中，模板文件转换为一个类，该类始终名为 `GeneratedTextTransformation`，它继承自 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  如果要改用其他方法集，您可以编写自己的类，然后在模板指令中指定该类。  您的类必须从 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 继承。  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 使用 `assembly` 指令可以引用已编译类所在的程序集。