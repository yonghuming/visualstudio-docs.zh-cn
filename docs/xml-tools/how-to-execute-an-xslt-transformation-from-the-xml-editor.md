---
title: "如何： 在 XML 编辑器中执行 XSLT 转换 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a432dabb09f3242ff3ba73527b86aac45e609588
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>如何：在 XML 编辑器中执行 XSLT 转换
通过“XML 编辑器”可以将 XSLT 样式表与 XML 文档关联，执行转换，以及查看输出。 由 XSLT 转换生成的输出显示在新的文档窗口中。  
  
 **输出**属性指定输出文件名。 如果**输出**属性为空白，则在临时目录中生成一个文件名。 文件扩展名基于样式表中的 `xsl:output` 元素，可以是 .xml、.txt 或 .htm。  
  
 如果**输出**属性指定的文件名为.htm 或.html 扩展，XSLT 输出预览使用[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]Internet 资源管理器。 所有其他文件扩展名将使用 [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio 选择的默认编辑器打开。 例如，如果文件扩展名为 .xml，Visual Studio 将使用“XML 编辑器”。  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>从 XML 文档执行 XSLT 转换  
  
1.  在“XML 编辑器”中打开 XML 文档。  
  
2.  将 XSLT 样式表与 XML 文档关联。  
  
    -   将 `xml-stylesheet` 处理指令添加到 XML 文档中。 例如，将以下行 `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` 添加到文档序言中。  
  
         - 或 -  
  
    -   添加 XSLT 样式表使用**属性**窗口。 在文档中**属性窗口**，单击**浏览**按钮**样式表**字段中选择 XSLT 样式表，然后单击**打开**.  
  
3.  单击**ShowXSL 输出**按钮上**XML 编辑器**工具栏。  
  
    > [!NOTE]
    >  如果没有与 XML 文档关联的样式表，对话框会提示您提供要使用的样式表。  
    >   
    >  由 XSLT 转换生成的输出显示在新的文档窗口中。  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>从 XSLT 样式表执行 XSLT 转换  
  
1.  在“XML 编辑器”中打开 XSLT 样式表。  
  
2.  指定 XML 文档中的**输入**字段的文档**属性**窗口。  
  
    > [!NOTE]
    >  XML 文档是用于转换的输入文档。 如果当启动 XSLT 转换时，不指定文档**文件打开**对话框随即显示，并且你可以在该时间在指定文档。  
  
3.  单击**ShowXSLT 输出**按钮上**XML 编辑器**工具栏。  
  
     由 XSLT 转换生成的输出显示在新的文档窗口中。  
  
### <a name="to-provide-a-different-output-file-name"></a>提供不同的输出文件名  
  
1.  指定文件的名称在**输出**字段的文档**属性**窗口。  
  
2.  单击**ShowXSLT 输出**按钮上**XML 编辑器**工具栏。  
  
     由 XSLT 转换生成的输出显示在新的文档窗口和输出窗口中使用的编辑器取决于的文件扩展名你**输出**文档属性。  
  
## <a name="see-also"></a>另请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)