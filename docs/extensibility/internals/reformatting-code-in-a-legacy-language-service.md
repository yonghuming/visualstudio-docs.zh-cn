---
title: "重新格式化旧语言服务中的代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b981430e9ce8f6bebf35d49fe1193f1d2097a715
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>重新格式化旧语言服务中的代码

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]源代码可以重新设置格式的规范化使用缩进和空格。 这可能包括插入或删除空格或在每个行开头的选项卡，添加行间情况下，新行或空格替换制表符或空格的选项卡。  
  
>**注意：**插入或删除换行字符可能会影响断点和书签，等的标记，但添加或删除空格或制表符不影响标记。  
  
用户可以通过选择启动 reformatting 操作**格式选择**或**格式文档**从**高级**上的菜单**编辑**菜单。 插入代码段或特定的字符时，也可以触发 reformatting 操作。 例如，当你键入 C# 中的右大括号，则匹配的左大括号和右大括号之间的所有内容是自动缩进到适当的级别。
  
当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]发送**格式选择**或**格式文档**命令到语言服务，<xref:Microsoft.VisualStudio.Package.ViewFilter>类调用<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>中的方法<xref:Microsoft.VisualStudio.Package.Source>类。 若要支持格式设置，必须重写<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法并提供你自己的格式设置代码。  
  
## <a name="enabling-support-for-reformatting"></a>重新格式化为启用支持  

若要支持的格式设置，`EnableFormatSelection`参数<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>必须设置为`true`时注册你的 VSPackage。 这将设置<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>属性`true`。 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>方法返回此属性的值。 如果它返回 true，<xref:Microsoft.VisualStudio.Package.ViewFilter>类调用<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>。  
  
## <a name="implementing-reformatting"></a>实现重新格式化

若要实现重新格式化，你必须从派生类<xref:Microsoft.VisualStudio.Package.Source>类并重写<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>对象描述要设置格式的范围和<xref:Microsoft.VisualStudio.Package.EditArray>对象保存在该范围上所做的编辑。 请注意，此范围可以是整个文档。 但是，因为不存在，可能需要多个跨度对所做的更改，应为可逆单个操作中的所有更改。 若要执行此操作，将包装中的所有更改<xref:Microsoft.VisualStudio.Package.CompoundAction>对象 （请参阅本主题中的"Using CompoundAction 类"部分）。

### <a name="example"></a>示例  

下面的示例确保有一个空格后每个逗号所选内容，除非逗号后跟一个选项卡，或位于行末尾。 删除在行中的最后一个逗号后尾随空格。 请参阅本主题以了解此方法从调用中的"使用 CompoundAction 类"一节<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>使用 CompoundAction 类  
 
所有重新格式化代码的一个部分完成应可逆在单一操作。 这可以实现使用<xref:Microsoft.VisualStudio.Package.CompoundAction>类。 此类包含一组的编辑操作对文本缓冲区到单个编辑操作。  
  
### <a name="example"></a>示例

下面是如何使用的一个示例<xref:Microsoft.VisualStudio.Package.CompoundAction>类。 请参阅本主题的示例中的"实现支持的格式设置"部分中的示例`DoFormatting`方法。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>另请参阅

[旧语言服务功能](legacy-language-service-features1.md)