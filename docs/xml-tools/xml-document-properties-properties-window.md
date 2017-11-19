---
title: "XML 文档属性，属性窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24f3760fb328331684e6894954d79675ff27494e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="xml-document-properties-properties-window"></a>XML 文档属性，“属性”窗口
**属性**窗口提供有关处于活动状态在 XML 编辑器中的文档的基本信息。 可用的属性取决于当前的活动 XML 文档的类型。  
  
> [!NOTE]
>  所有 XML 文档属性均保存在该解决方案中。 因此，下次打开该解决方案时，不必重新输入这些值。  
  
 **编码**  
 文件的字符编码。 更改此属性将同时更改 XML 声明的编码属性，反之亦然。 新编码将用于在保存文件时为文件编码。  
  
 **输入**  
 与 XSLT 样式表关联的输入文档。 它由**ShowXSLT 输出**命令。 可以使用浏览选择文档 (**...**) 按钮。  
  
 只有 XSLT 文件在“编辑器”窗口中当前处于活动状态时，才会显示此属性。  
  
 **输出**  
 转换 XML 文档时生成的文件。  
  
 如果未指定文件，将根据 `method` 元素的 `xsl:output` 属性生成默认的文件名，该属性确定文件的扩展名。 默认的文件位于当前用户的临时目录。  
  
 **架构**  
 用于验证的架构。 此按钮将打开**XSD 架构**对话框中，可以用于选择要使用的架构。  
  
 也可以输入架构的路径。 如果指定了多个架构，每个架构路径必须加双引号。  
  
 **样式表**  
 用于转换文档的 XSLT 文件时**显示 XSLT 输出**使用命令。 如果时，此字段为空白**显示 XSLT 输出**命令时，编辑器使用中提供的值`xml-stylesheet`处理指令的文档，或它提示你输入文件名。  
  
 在编辑 XSLT 文件时，可以使用此属性指定应是不同的样式表时使用**显示 XSLT 输出**或**调试 XSLT**选择命令。 例如，如果正在编辑的样式表包含在父样式表中，则可能需要这样做。  
  
## <a name="see-also"></a>另请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)   
 [“XML 编辑器”的组件](../xml-tools/xml-editor-components.md)