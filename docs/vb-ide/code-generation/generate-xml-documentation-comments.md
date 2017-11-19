---
title: "生成 XML 文档注释的代码生成 (Visual Basic 中) |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1291667c7acb47abe543d275549179abea0c8467
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>在 Visual Basic 中生成 XML 文档注释
**新增功能：**便会立即生成 XML 文档所选的元素所需的基。 

**何时：**你想要创建 XML 文档注释以供将来处理由 Sandcastle 之类的文档工具。

**原因：**你可以手动整个注释块自己创建，但这将节省时间并提高准确性通过生成的基本模板和其他元素。 

**如何：**

1. 将文本光标置于想要记录，例如，一种方法的元素。

   ![到文档的方法](media/doc_highlight.png)

1. 接下来，键入**''** （3 单引号） 的自动将根据需要创建基模板和其他元素。  例如，如果注释方法，它将生成**\<摘要\>**标记以及 **\<param\>** 的是每个参数的标记传递给方法，和一个**\<返回\>**以记录该方法返回的标记。

   ![模板](media/doc_preview.png)

1. 完成注释，添加，就需要你认为任何其他信息。

   ![已完成的注释](media/doc_result.png)

## <a name="see-also"></a>另请参阅
[使用 XML (Visual Basic 中) 将代码文档化](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[代码生成 (Visual Basic)](../code-generation-vb.md) 