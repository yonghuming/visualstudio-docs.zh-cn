---
title: "Visual Studio 中的 XML 工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3786e74f9913400e7a95d962c8512d2263d6ae39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio 中的 XML 工具
*可扩展标记语言 (XML)*是一种为说明数据提供了一种格式的标记语言。 该语言使跨越多个平台进行更准确的内容声明和获得更有意义的搜索结果变得更加容易。 此外，XML 实现了表示与数据的分离。 例如，在 HTML 中，使用标记来告诉浏览器将数据显示为粗体或斜体；而在 XML 中，标记只用于描述数据，例如城市名、温度和大气压。 在 XML 中，使用样式表（例如，可扩展样式表语言 (XSL) 和层叠样式表 (CSS)）在浏览器中显示数据。 XML 将数据与表示及处理相分离。 这一特点使你能够通过应用不同的样式表和应用程序，按照所需的方式显示和处理数据。  
  
 XML 是为在 Web 上传送而优化了的 SGML 的子集。 它是由万维网联合会 (W3C) 定义的。 此标准化确保了结构化数据的统一性和相对于应用程序或供应商的独立性。  
  
 XML 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的许多功能的核心。 下面的主题列表列出了 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中提供的与 XML 相关的工具和功能。  
  
 有关详细信息，请参阅[XML 开发人员中心](http://go.microsoft.com/fwlink/?LinkID=100176)，这为 XML 开发人员提供的最新文档、 技术信息、 下载、 新闻组和其他资源。  
  
## <a name="in-this-section"></a>本节内容  
 [使用 XML 数据](../xml-tools/working-with-xml-data.md)  
 讨论 XML 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的数据处理方面的作用。  
  
 [调试 XSLT](../xml-tools/debugging-xslt.md)  
 提供相关主题的链接，这些主题介绍如何使用 Visual Studio 调试器调试 XSLT。  
  
## <a name="reference"></a>参考  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 公开[XML 编辑器](http://go.microsoft.com/fwlink/?LinkId=228249)分析通过树[System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250)对任何 XML 文档。  
  
 [XML 标准参考](http://msdn.microsoft.com/en-us/79c78508-c9d0-423a-a00f-672e855de401)  
 提供有关 XML 技术的信息，其中包括 XML、文档类型定义 (DTD)、XML 架构定义语言 (XSD) 和 XSLT。  
  
 <xref:System.Xml?displayProperty=fullName>  
 描述组成 <xref:System.Xml> 命名空间的类和其他元素，并提供转到每一项的更详细信息的链接。  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 描述组成 <xref:System.Xml.Serialization> 命名空间的类和其他元素，并提供指向有关每一项的更详细信息的链接。  
  
## <a name="related-sections"></a>相关章节  
 [XML 文档对象模型 (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)  
 描述 <xref:System.Xml.XmlDocument> 及其关联类如何遵从 W3C 文档对象模型 (Core) 等级 1 和等级 2 命名空间支持规范。  
  
 [读取具有 XmlReader XML](http://msdn.microsoft.com/en-us/3029834c-a27e-4331-b7aa-711924062182)  
 描述 <xref:System.Xml.XmlReader> 如何通过 XML 流提供对 XML 数据的非缓存只进只读访问。  
  
 [写入具有 XmlWriter XML](http://msdn.microsoft.com/en-us/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 描述 <xref:System.Xml.XmlWriter> 如何提供生成 XML 流的非缓存只进方法，并帮助你生成符合 W3C 标准的 XML 文档。  
  
 [XSLT 转换](/dotnet/standard/data/xml/xslt-transformations)  
 描述 <xref:System.Xml.Xsl.XslCompiledTransform> 类如何实现 XSLT 1.0 建议。  
  
 [使用 XPath 数据模型处理 XML 数据](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
 描述 <xref:System.Xml.XPath.XPathNavigator> 类怎样才能处理 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象中存储的 XML 数据。 <xref:System.Xml.XPath.XPathNavigator> 类以 XQuery 1.0 和 XPath 2.0 数据模型为基础，可用于导航和编辑 XML 数据。  
  
 [XML 架构对象模型 (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)  
 通过提供 <xref:System.Xml.Schema.XmlSchema> 类来加载和编辑架构，描述了用于创建和操作 XML 架构的类。