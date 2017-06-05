---
title: "使用针对 Visual Studio 的 R 工具创建 R Markdown | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 972abfcfda570d66b1b15b25b16e68157fc73b81
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---

# <a name="creating-r-markdown-documents"></a>创建 R Markdown 文档

R Markdown（参见 [rmarkdown.rstudio.com](https://rmarkdown.rstudio.com/)）是一种文档格式，可将 R 中的分析转化为高质量的文档、报告、演示文稿和仪表板。

针对 Visual Studio 的 R 工具提供了 R Markdown 项模板、编辑器支持（包括编辑器中适用于 R 代码的 IntelliSense）和文件生成功能。

使用 R Markdown：

1. 关闭 Visual Studio。
1. （仅一次）从 [pandoc.org](http://pandoc.org/installing.html) 安装 pandoc。
1. 重启 Visual Studio，它应该获取 pandoc 安装程序。
1. 安装 `knitr` 和 `rmarkdown` 包，可从[交互窗口](interactive-repl.md)执行安装操作：

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. 使用“文件”>“新建”菜单命令，并从列表中选择“R Markdown”创建新 R Markdown 文件，或者在解决方案资源管理器中右键单击项目，选择“添加 R Markdown”（或使用“添加”>“新项...”，并从列表中选择“R Markdown”）。

1. 新文件的默认内容如下：

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---
    
    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.
    
    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
    
    ```{r}
    summary(cars)
    ```
    
    You can also embed plots, for example:
    
    ```{r, echo=FALSE}
    plot(cars)
    ```
    
    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
    
    ~~~

1. 编辑时，右键单击编辑器，然后选择“预览”，其中包含 HTML、PDF 和 Microsoft Word 选项。 可从该预览根据所选格式保存文件。

