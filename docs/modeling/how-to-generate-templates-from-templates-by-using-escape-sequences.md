---
title: "如何：使用转义序列从模板生成模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文本模板, 根据模板生成模板"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 35
---
# 如何：使用转义序列从模板生成模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建的文本模板可以创建另一个文本模板作为其生成的文本输出。  为此，必须使用转义序列来描述文本模板标记。  如果不使用转义序列，则生成的文本模板会具有预定义含义。  有关在文本模板中使用转义序列的更多信息，请参见[在文本模板中使用转义序列](../modeling/using-escape-sequences-in-text-templates.md)。  
  
### 从文本模板内生成文本模板  
  
-   对于单独的文本模板文件中的指令、语句、表达式和类功能，使用反斜杠 \(\\\) 作为转义字符可在文本模板中生成必需的标记。  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## 示例  
 下面的示例使用转义字符从文本模板生成文本模板。  `output` 指令将目标文件类型设置为文本模板文件类型（.tt）。  
  
```c#  
\<#@ output extension=".tt" \#>  
\<#@ assembly name="System.Xml.dll" \#>  
\<#@ import namespace="System.Xml" \#>  
\<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {\#>  
           \<#= attr.Name \#>  
       \<#}  
     }  
\#>  
```  
  
 生成的文本输出为文本模板。  
  
```  
<#@ output extension=".tt" #>  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {#>  
           <#= attr.Name #>  
       <#}  
     }  
#>  
```