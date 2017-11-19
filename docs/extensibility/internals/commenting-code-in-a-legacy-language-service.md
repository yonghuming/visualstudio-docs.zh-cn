---
title: "在旧语言服务中的注释代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8952612c9502704f79410461d29ca8ab87fa3ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="commenting-code-in-a-legacy-language-service"></a>在旧语言服务中的注释代码
编程语言通常提供一种添加批注或注释代码的方法。 注释是文本来提供有关代码的其他信息，但在编译或解释期间将忽略某一部分。  
  
 托管的包框架 (MPF) 类为注释和 uncommenting 所选文本提供支持。  
  
## <a name="comment-styles"></a>注释样式  
 有两种常规样式的注释：  
  
1.  其中注释是在单独的行的行注释。  
  
2.  块注释，注释可以包含多个行的位置。  
  
 行注释通常具有起始字符 （或字符），块注释时具有开始和结束字符。 例如，在 C# 中，行注释开头 / /，和块注释开头 / * 和结束的\*/。  
  
 当用户选择命令**注释选定内容**从**编辑** -> **高级**菜单上，该命令路由到<xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>方法<xref:Microsoft.VisualStudio.Package.Source>类。 当用户选择命令**取消注释所选内容**，该命令路由到<xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>方法。  
  
## <a name="supporting-code-comments"></a>支持的代码注释  
 你可以通过你语言服务支持代码注释`EnableCommenting`命名的参数<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。 这将设置<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>属性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。 有关设置 servicce 功能的语言的详细信息，请参阅[注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md))。  
  
 你还必须重写<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法以返回<xref:Microsoft.VisualStudio.Package.CommentInfo>结构与你的语言的注释字符。 C# 的样式行注释字符是默认值。  
  
### <a name="example"></a>示例  
 下面是示例实现<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>方法。  
  
```csharp  
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
  
## <a name="see-also"></a>另请参阅  
 [旧语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)