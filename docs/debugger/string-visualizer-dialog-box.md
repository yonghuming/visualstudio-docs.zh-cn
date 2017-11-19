---
title: "字符串可视化工具中查看字符串 |Microsoft 文档"
ms.custom: 
ms.date: 07/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a14b9f68eb2f77ed248c82b81ce7063547e58bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>在 Visual Studio 中的字符串可视化工具中查看字符串
虽然你进行调试，你可以打开到太长，在数据提示或调试器窗口中查看的查看字符串的字符串可视化工具。 在许多情况下，可视化工具可以帮助您标识格式不正确的字符串。

内置的标准字符串可视化工具包括纯文本、 XML、 HTML 和 JSON。 用于几个其他类型，如出现在调试器中的 WPF 对象 windows 喜欢**自动**窗口中，你也可以打开可视化工具。

## <a name="open-a-string-visualizer"></a>打开字符串可视化工具

若要查看的纯文本、 XML、 HTML 或 JSON 字符串，请单击放大镜图标![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "可视化工具图标")当悬停在包含一个字符串值的变量。 你必须在调试器中，若要查看的放大镜图标暂停。

![打开字符串可视化工具](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>查看字符串数据

**表达式**字符串可视化工具中的字段在调试器中显示的当前变量或表达式悬停在。

**值**字段显示的字符串值。 文本可视化工具显示纯文本。

空白**值**指示特定可视化工具无法识别的字符串类型。 例如，XML 可视化工具显示空白**值**为简单文本字符串 （具有无 XML 标记） 或 JSON 格式的字符串。 如果你需要在可视化工具中查看无法识别的字符串，使用文本可视化工具。

### <a name="view-json-string-data"></a>查看 JSON 字符串数据

格式正确的 JSON 字符串将显示类似于下图在 JSON 可视化工具中。 格式不正确的 JSON 可能会显示错误图标 （或如果无法识别的空白）。

![JSON 字符串可视化工具](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 字符串可视化工具")

### <a name="view-xml-string-data"></a>查看 XML 字符串数据

格式正确的 XML 字符串将显示类似于下图在 XML 可视化工具中。 XML 格式不正确可能会显示不带 XML 标记 （或如果无法识别的空白）。

![XML 字符串可视化工具](../debugger/media/dbg-string-visualizers-xml.png "XML 字符串可视化工具")

### <a name="view-html-string-data"></a>查看 HTML 字符串数据

格式正确的 HTML 字符串看起来类似于你将看到是否字符串将呈现在浏览器中，如下面的插图中所示的视图。 格式不正确的 HTML 可能显示为纯文本。

![HTML 字符串可视化工具](../debugger/media/dbg-string-visualizers-html.png "HTML 字符串可视化工具")

## <a name="see-also"></a>另请参阅  
 [创建自定义可视化工具 （C#、 Visual Basic）](../debugger/create-custom-visualizers-of-data.md)