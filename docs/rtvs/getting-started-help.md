---
title: "针对 Visual Studio 的 R 工具中的帮助窗口 | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
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
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>针对 Visual Studio 的 R 工具中的帮助

在 Visual Studio 中，R 的相关帮助直接集成到交互窗口中。 每当使用 `?` 命令（如`?mtcars`）时，Visual Studio 窗口中都会显示 R 文档提供的帮助：

![Visual Studio 中的帮助窗口](~/docs/rtvs/media/help-window.png)

> [!Tip]
> 与 Visual Studio 中的所有其他窗口一样，可按照任意喜欢的方式排列和停靠帮助窗口。 请参阅[在 Visual Studio 中自定义窗口布局](../ide/customizing-window-layouts-in-visual-studio.md)。
>
> 要在浏览器中打开帮助结果，还可选择“R 工具”>“选项”菜单，并将“R 帮助浏览器”属性设置为 `External`。 请参阅[选项](options.md)。

若要搜索帮助，请使用 `??` 命令，如果搜索词包含空格，请将其放入引号中：

```R
??"Motor Trend"
```

![帮助搜索结果](~/docs/rtvs/media/help-search1.png)

帮助窗口还包括一个搜索输入字段，可通过该字段直接在 R 文档中进行进一步搜索：

![使用输入字段的帮助搜索结果](~/docs/rtvs/media/help-search2.png)

## <a name="integrated-help-lookup"></a>集成帮助查找

由于开发人员经常在 R 文档中搜索有关函数名称、数据集和其他元素的帮助，因此，针对 Visual Studio 的 R 工具将帮助查找直接集成到编辑器和交互窗口中，简化了这一过程。

- 如果在自动完成操作期间按 F1，将生成一个列表，列出与子字符串匹配的帮助结果。
- 右键单击搜索词（如某个函数），然后选择“相关帮助”命令，或只需按 F1，即可打开该函数的帮助。 还可对任何选定内容调用“相关帮助”。

    ![通过右键单击上下文菜单调用帮助](~/docs/rtvs/media/help-right-click.png)

> [!Tip]
> 若要在浏览器中打开集成帮助，请选择“R 工具”>“选项”，并将“F1 Web 浏览器”设置为 `External`。 请参阅[选项](options.md)。

## <a name="integrated-stackoverflow-search"></a>集成的 StackOverflow 搜索

除了在 R 文档中搜索外，开发人员在编写代码时还经常搜索 StackOverflow。 RTVS 也简化了该过程。 如果单击某个词或选定内容，并选择“在 Web 中搜索”命令，或只是按 Ctrl+F1，将打开 Visual Studio 窗口（或者如果更改了“F1 Web 浏览器”选项，则会打开浏览器），默认情况下，其中包含 StackOverflow 范围内该词的搜索结果：

![Visual Studio 中的 Web 搜索结果](~/docs/rtvs/media/help-web-search-results.png)

可通过“R 工具”>“选项”>“F1 Web 搜索字符串”选项更改追加的字符串 `R site:stackoverflow`：

![更改 F1 Web 搜索字符串选项](~/docs/rtvs/media/options-dialog.png)
