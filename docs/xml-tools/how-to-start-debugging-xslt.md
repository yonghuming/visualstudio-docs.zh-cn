---
title: "如何： 开始调试 XSLT |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: 087d51eee11597b1e637ce860faecdd3a21ce7af
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-start-debugging-xslt"></a>如何：开始调试 XSLT
可以使用 XSLT 调试器来调试 XSLT 样式表或 XSLT 应用程序。 在调试时，可以通过进入并逐行执行代码、逐行执行代码或跳出代码来一次执行一行代码。 XSLT 调试程序和其他 Visual Studio 调试程序中使用代码逐行执行功能的命令都相同。 开始调试后，XSLT 调试器即会打开窗口以显示输入文档和 XSLT 输出。  
  
## <a name="xml-editor"></a>XML 编辑器  
 可以从“XML 编辑器”启动调试程序。 这样可以在设计样式表时进行调试。  
  
#### <a name="to-start-debugging-from-a-style-sheet"></a>从样式表开始调试  
  
1.  在“XML 编辑器”中打开样式表。  
  
2.  选择**调试 XSL**从**XML**菜单。  
  
#### <a name="to-start-debugging-from-an-xml-input-document"></a>从 XML 输入文档开始调试  
  
1.  在 XML 编辑器中打开 XML 文档。  
  
2.  选择**调试 XSL**从**XML**菜单。  
  
## <a name="xslt-from-other-languages"></a>其他语言的 XSLT  
 也可以在调试应用程序的同时进入并逐行执行 XSLT。 在 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> 调用中按 F11 键时，调试程序可以进入并逐行执行 XSLT 代码。  
  
> [!NOTE]
>  不支持从 <xref:System.Xml.Xsl.XslTransform> 类进入并逐行执行 XSLT。 <xref:System.Xml.Xsl.XslCompiledTransform> 类是唯一支持在调试的同时进入并逐行执行 XSLT 的 XSLT 处理器。  
  
#### <a name="to-start-debugging-an-xslt-application"></a>开始调试 XSLT 应用程序  
  
1.  在实例化 <xref:System.Xml.Xsl.XslCompiledTransform> 对象时，在代码中将 `enableDebug` 参数设置为 `true`。  
  
     此设置通知 XSLT 处理器在编译代码时创建调试信息。  
  
2.  按 F11 键进入并逐行执行 XSLT 代码。  
  
     XSLT 样式表加载到新的文档窗口中，XSLT 调试程序也将启动。  
  
     或者，可以将断点添加到样式表并运行应用程序。  
  
### <a name="example"></a>示例  
 下面是一个 C# XSLT 程序的示例。 该示例显示如何启用 XSLT 调试。  
  
```csharp
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
  
namespace ConsoleApplication   
{  
  class Program   
  {  
    private const string sourceFile = @"c:\data\xsl_files\books.xml";  
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";  
    private const string outputFile = @"c:\data\xsl_files\output.xml";  
  
    static void Main(string[] args)  
    {  
      // Enable XSLT debugging.  
      XslCompiledTransform xslt = new XslCompiledTransform(true);  
  
      // Compile the style sheet.  
      xslt.Load(stylesheet)  
  
      // Execute the XSLT transform.  
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);  
      xslt.Transform(sourceFile, null, outputStream);  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [演练： 调试 XSLT 样式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)   
 [代码单步执行概述](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9)