---
title: "文本模板实用工具方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: "50"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 534a7317b4bca2abe559c028d025a52997a9f508
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="text-template-utility-methods"></a>文本模板实用工具方法
有多种方法中编写代码时都可供你[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文本模板。 这些方法定义中<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  
  
> [!TIP]
>  你还可以使用其他方法和由正则 （不预处理） 文本模板中的主机环境提供的服务。 例如，你可以解析文件路径、 记录错误，并获取所提供的服务[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和任何加载包。  有关详细信息，请参阅[从文本模板访问 Visual Studio](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4)。  
  
## <a name="write-methods"></a>编写方法  
 你可以使用`Write()`和`WriteLine()`方法要追加了标准的代码块，而不是使用表达式代码块中的文本。 下面的两个代码块在功能上等效。  
  
##### <a name="code-block-with-an-expression-block"></a>与将表达式块的代码块  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>使用 WriteLine() 的代码块  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 你可能会发现有助于而不是在具有嵌套的控制结构长的代码块将表达式块中使用这些实用程序方法之一。  
  
 `Write()`和`WriteLine()`方法具有两种重载，其中一个采用单个字符串参数和一个使用复合格式字符串以及要包含在字符串中的对象的数组 (如`Console.WriteLine()`方法)。 以下两种用法`WriteLine()`在功能上等效：  
  
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
  
## <a name="indentation-methods"></a>缩进方法  
 缩进方法可用于设置格式的文本模板的输出。 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>类具有`CurrentIndent`字符串显示当前的缩进文本模板中的属性和`indentLengths`字段，它是已添加的缩进的列表。 你可以添加与缩进`PushIndent()`方法减少与缩进`PopIndent()`方法。 如果你想要删除所有的缩进，使用`ClearIndent()`方法。 下面的代码块显示使用这些方法：  
  
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
  
 此代码块生成以下输出：  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>错误和警告方法  
 你可以使用错误和警告实用程序方法添加到消息[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]错误列表。 例如，下面的代码会将一条错误消息添加到的错误列表。  
  
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
  
## <a name="access-to-host-and-service-provider"></a>对主机和服务提供程序的访问  
 属性`this.Host`可以提供对属性执行模板的宿主公开访问。 若要使用`this.Host`，必须设置`hostspecific`属性中`<@template#>`指令：  
  
 `<#@template ... hostspecific="true" #>`  
  
 一种`this.Host`取决于在其中执行模板的宿主类型。 在模板中运行[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，可以强制转换`this.Host`到`IServiceProvider`来访问服务，例如 IDE。 例如：  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>使用一组不同的实用工具方法  
 作为文本生成过程的一部分，你的模板文件转换为一个类，这始终名为`GeneratedTextTransformation`并继承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。 如果你想要使用不同设置的方法而不是，你可以编写您自己的类，并在模板指令中指定它。 你的类必须继承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 使用`assembly`指令以引用程序集可以找到已编译的类。