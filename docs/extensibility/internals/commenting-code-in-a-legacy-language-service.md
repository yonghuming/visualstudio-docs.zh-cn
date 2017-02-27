---
title: "旧语言服务中的注释代码 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "注释，支持的语言服务 [托管的包框架]"
  - "注释代码的语言服务 [托管的包框架]"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 旧语言服务中的注释代码
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

编程语言通常提供方法说明或注释代码。  注释是提供有关代码的附加信息文本的部分，但在编译或解释时被忽略。  
  
 托管包框架 \(MPF\)类提供对注释和取消注释选定的文本支持。  
  
## 注释样式  
 包含注释两个泛型样式:  
  
1.  行注释，这些注释在一行。  
  
2.  块注释，注释可以包含多个行。  
  
 ，当块注释具有开始时间和结束字符时，行注释通常具有开始字符 \(或字符\)。  例如，在 c\# 中，行注释从 \/\/，开始，从而阻止注释以\/\* 和结束开始使用 \*。  
  
 当用户选择命令 **注释选择** 从 **编辑** \- 时 AMP\_GT **高级** 菜单，命令传送到 <xref:Microsoft.VisualStudio.Package.Source> 类的 <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> 方法。  当用户选择命令 **取消注释选择**时，命令路由到 <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> 方法。  
  
## 支持代码注释  
 可以使语言服务通过名为 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 参数的 `EnableCommenting` 支持代码注释。  这将设置 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类的 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> 属性。  有关设置语言 servicce 功能的更多信息，请参见 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)\)。  
  
 您还必须重写 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 方法返回包含注释字符的一 <xref:Microsoft.VisualStudio.Package.CommentInfo> 结构该语言的。  c\# 样式行注释字符是默认设置。  
  
### 示例  
 这是 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 方法的示例实现。  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## 请参阅  
 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)