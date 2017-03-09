---
title: "Visual Studio 中的 XML 工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "类 [Visual Studio], XML"
  - "CSS, 用于 XML 的样式表"
  - "数据 [Visual Studio], XML"
  - "数据集 [Visual Basic], XML 架构"
  - "发现文件, XML"
  - "企业级模板, XML 和"
  - "服务器控件, XML 和"
  - "SGML, XML"
  - "样式表, 对于 XML"
  - "Web 服务器控件, XML"
  - "Web 服务"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], .NET Framework 类"
  - "XML [Visual Studio], 数据源"
  - "XML [Visual Studio], 资源"
  - "XML [Visual Studio], SGML 关系"
  - "XML 架构"
  - "XMLDataDocument 类"
  - "XSD 架构"
  - "XSL"
  - "XSL, 样式表"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual Studio 中的 XML 工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*可扩展标记语言 \(XML\)* 是一种提供数据描述格式的标记语言。  该语言使跨越多个平台进行更准确的内容声明和获得更有意义的搜索结果变得更加容易。  此外，XML 实现了表示与数据的分离。  例如，在 HTML 中，使用标记来告诉浏览器将数据显示为粗体或斜体；而在 XML 中，标记只用于描述数据，例如城市名、温度和大气压。  在 XML 中，使用样式表（例如，可扩展样式表语言 \(XSL\) 和层叠样式表 \(CSS\)）在浏览器中显示数据。  XML 将数据与表示及处理相分离。  这一特点使你能够通过应用不同的样式表和应用程序，按照所需的方式显示和处理数据。  
  
 XML 是为在 Web 上传送而优化了的 SGML 的子集。  它是由万维网联合会 \(W3C\) 定义的。  此标准化确保了结构化数据的统一性和相对于应用程序或供应商的独立性。  
  
 XML 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的许多功能的核心。  下面的主题列表列出了 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中提供的与 XML 相关的工具和功能。  
  
 有关详细信息，请参阅 [XML 开发中心](http://go.microsoft.com/fwlink/?LinkID=100176)，该网站为 XML 开发人员提供了最新的文档、技术信息、下载、新闻组以及其他资源。  
  
## 本节内容  
 [使用 XML 数据](../xml-tools/working-with-xml-data.md)  
 讨论 XML 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的数据处理方面的作用。  
  
 [调试 XSLT](../xml-tools/debugging-xslt.md)  
 提供相关主题的链接，这些主题介绍如何使用 Visual Studio 调试器调试 XSLT。  
  
## 参考  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 对任何 XML 文档，都通过 [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) 公开 [XML 编辑器](http://go.microsoft.com/fwlink/?LinkId=228249)分析树。  
  
 [XML 标准参考资料](http://msdn.microsoft.com/zh-cn/79c78508-c9d0-423a-a00f-672e855de401)  
 提供有关 XML 技术的信息，其中包括 XML、文档类型定义 \(DTD\)、XML 架构定义语言 \(XSD\) 和 XSLT。  
  
 <xref:System.Xml?displayProperty=fullName>  
 描述组成 <xref:System.Xml> 命名空间的类和其他元素，并提供转到每一项的更详细信息的链接。  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 描述组成 <xref:System.Xml.Serialization> 命名空间的类和其他元素，并提供指向有关每一项的更详细信息的链接。  
  
## 相关章节  
 [XML 文档对象模型 \(DOM\)](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 描述 <xref:System.Xml.XmlDocument> 及其关联类如何遵从 W3C 文档对象模型 \(Core\) 等级 1 和等级 2 命名空间支持规范。  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/zh-cn/3029834c-a27e-4331-b7aa-711924062182)  
 描述 <xref:System.Xml.XmlReader> 如何通过 XML 流提供对 XML 数据的非缓存只进只读访问。  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/zh-cn/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 描述 <xref:System.Xml.XmlWriter> 如何提供生成 XML 流的非缓存只进方法，并帮助你生成符合 W3C 标准的 XML 文档。  
  
 [XSLT 转换](../Topic/XSLT%20Transformations.md)  
 描述 <xref:System.Xml.Xsl.XslCompiledTransform> 类如何实现 XSLT 1.0 建议。  
  
 [使用 XPath 数据模型处理 XML 数据](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 描述 <xref:System.Xml.XPath.XPathNavigator> 类怎样才能处理 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象中存储的 XML 数据。  <xref:System.Xml.XPath.XPathNavigator> 类以 XQuery 1.0 和 XPath 2.0 数据模型为基础，可用于导航和编辑 XML 数据。  
  
 [XML 架构对象模型 \(SOM\)](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 通过提供 <xref:System.Xml.Schema.XmlSchema> 类来加载和编辑架构，描述了用于创建和操作 XML 架构的类。