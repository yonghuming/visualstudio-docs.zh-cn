---
title: "CA3077: API 设计、 XML 文档和 XML 文本读取器中的不安全处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6944b49626771317f1643f7ae521b0db43c2200c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077：API 设计、XML 文档和 XML 文本读取器中的不安全处理
|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|类别|Microsoft.Security|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 当设计派生自 XMLDocument 和 XMLTextReader 的 API 时，请注意 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>。  当引用或解析外部实体源或设置 XML 中的不安全值时，使用不安全的 DTDProcessing 实例可能会导致信息泄露。  
  
## <a name="rule-description"></a>规则说明  
 XML 分析器可以通过两种方式确定文档有效性， [文档类型定义 (DTD)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) 是其中一种（根据  [万维网联合会 (W3C) 可扩展标记语言 (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)的定义）。 此规则查找接受不受信任数据的某些属性和实例以提醒开发人员有关的潜在 [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) 威胁，该威胁可能会导致 [拒绝服务 (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) 攻击。 在以下情况下触发此规则：  
  
-   <xref:System.Xml.XmlDocument>或<xref:System.Xml.XmlTextReader>类使用默认冲突解决程序值进行 DTD 处理。  
  
-   没有为 XmlDocument 或 XmlTextReader 派生类定义的构造函数或没有用于 <xref:System.Xml.XmlResolver>的安全值。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
  
-   捕获和处理所有 XmlTextReader 异常正确以避免路径信息泄露。  
  
-   使用<xref:System.Xml.XmlSecureResolver>而不是 XmlResolver 来限制 XmlTextReader 可以访问的资源。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 除非确信已知道输入是来自受信任的源，否则请勿禁止显示此警告的规则。  
  
## <a name="pseudo-code-examples"></a>伪代码示例  
  
### <a name="violation"></a>冲突  
  
```csharp  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass () {} // warn   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2() // warn   
        {   
        }   
    }   
}  
```  
  
### <a name="solution"></a>解决方案  
  
```csharp  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass ()    
        {   
            XmlResolver = null;   
        }   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2()    
        {   
               XmlResolver = null;   
        }   
    }   
}  
```