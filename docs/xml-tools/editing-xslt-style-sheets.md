---
title: "编辑 XSLT 样式表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a10bcadbffef1f67086263762f292765c932a986
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="editing-xslt-style-sheets"></a>编辑 XSLT 样式表
“XML 编辑器”还可以用于编辑 XSLT 样式表。 可以利用默认的编辑器功能，例如 IntelliSense、大纲、XML 代码段等。 此外，还提供了一些新功能，使 XSLT 中的开发更加容易。  
  
## <a name="xslt-features"></a>XSLT 功能  
 下表介绍使用 XSLT 样式表时的特定功能。  
  
 **语法着色**  
 XSLT 关键字，如`template`， `match`，依此类推，显示在指定的 XSLT 关键字颜色**字体和颜色**设置。  
  
 **波浪下划线**  
 “XML 编辑器”使用已安装的 xslt.xsd 文件验证 XSLT 样式表。 验证错误以蓝色的波浪形下划线显示。 “XML 编辑器”还在后台编译样式表，并使用相应的波浪形下划线报告编译器错误或警告。  
  
 **对脚本块的支持**  
 XSLT 调试程序支持脚本块中的代码，这样，你可以设置断点并逐行执行脚本块代码。  
  
 **查看 XSLT 输出**  
 可以在“XML 编辑器”中执行 XSL 转换并查看输出。 有关详细信息，请参阅[如何： 从 XML 编辑器中执行 XSLT 转换](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)。  
  
 **调试 XSLT**  
 可以在“XML 编辑器”中从 XSLT 文件启动 XSLT 调试程序。 调试程序支持在 XSLT 文件中设置断点、查看 XSLT 执行状态等。 将光标置于 XSLT 变量上，可以显示包含变量值的工具提示。 调试程序可以用于调试样式表，也可以用于调试从另一个应用程序调用的已编译 XSLT 转换。 有关详细信息，请参阅[调试 XSLT](../xml-tools/debugging-xslt.md)。  
  
## <a name="see-also"></a>另请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)