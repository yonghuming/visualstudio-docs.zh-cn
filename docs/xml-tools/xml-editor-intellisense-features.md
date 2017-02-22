---
title: "XML 编辑器的 IntelliSense 功能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML 编辑器的 IntelliSense 功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 编辑器提供了完整的 IntelliSense 功能，可与 Visual Studio 中提供的其他语言编辑器相提并论。本节介绍如何使用 XML 架构定义语言 \(XSD\) 和 XSLT 文档中的 IntelliSense。  
  
## XSD 文档中的 IntelliSense  
 架构与文档关联之后，可随时键入 `"<"` 或单击 XML 编辑器工具栏上的**“显示对象成员列表”**按钮来获得预期元素的下拉列表。有关如何将架构与 XML 文档相关联的信息，请参见 [XML 文档验证](../xml-tools/xml-document-validation.md)。  
  
 在开始标记内键入空格时也可以获得一个下拉列表，其中显示可以添加到当前元素中的所有特性。  
  
 在为特性值键入 `"="` 时或为值键入左引号时，也可以获得该特性的可能值的列表。仅当架构通过 `xsd:enumeration` 方面提供枚举值时或特性属于 `Boolean` 类型时，才会提供值。对于 `xml:lang` 或任何从 `xsd:language` 派生的 `simpleType`，还提供已知语言代码的智能感知列表。对于命名空间声明，会提供已知 `targetNamespace` 值的智能感知列表。  
  
 如果元素为 `simpleType`，在键入 `">"` 封闭开始标记时，也会提供可能的值的 IntelliSense 列表。元素的行为类似于上一段中所述的特性的行为。  
  
 根据在关联的架构中发现的 `xsd:annotation` 和 `xsd:documentation` 信息，还会在这些 IntelliSense 列表上显示工具提示。  
  
## XSLT 文档中的 IntelliSense  
 将命名模板或特性添加到 XSLT 文档中之后，便可以使用 IntelliSense 插入以下内容：  
  
-   特性集名称。  
  
-   模板模式。  
  
-   模板名称。  
  
-   给定模式的参数名称。  
  
-   给定命名模板的参数名称。  
  
 有关更多信息，请参见[演练：使用 XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) 主题。  
  
## 自动完成  
 XML 编辑器还通过为您填写所需的 XML 语法来使编辑 XML 更加容易。例如，如果您键入以下开始标记：  
  
 `<book>`  
  
 “XML 编辑器”将填写结束标记，并将光标置于开始标记之后。以下是这种情况的示例（“&#124;”指示光标位置）：  
  
 `<book>`&#124;`</book>`  
  
 因为属性值必须总是加引号，“XML 编辑器”会为您填写引号。例如，如果您键入以下内容：  
  
 `<book title=`  
  
 “XML 编辑器”会添加引号并将光标置于两个引号之间：  
  
 `<book title="`&#124;`"`  
  
 同样，“XML 编辑器”还为您自动插入以下 XML 语法：  
  
-   结束处理指令：`?>`  
  
-   结束 CDATA 块：`]]>`  
  
-   结束注释：`-->`  
  
-   结束 DTD 声明：`>`  
  
 如果从智能感知列表中选择了命名空间限定的元素或特性，并且该元素或特性的命名空间尚不在相应范围内，“XML 编辑器”还可以插入命名空间声明。  
  
 例如，如果从智能感知列表中选择了 `e:Book` 元素，该元素的前缀绑定到的 `http://books` 命名空间尚未在文档中声明，“XML 编辑器”将为您插入所需的命名空间声明。以下是生成的 XML 文本：  
  
 `<e:Book xmlns:e="http://books"`  
  
## 括号匹配  
 “XML 编辑器”提供括号突出显示功能，针对您刚封闭的元素提供即时反馈。您也可以使用快捷键 \(CTRL\+\]\) 从一个括号跳转到匹配的括号。  
  
 “XML 编辑器”对下列项执行此操作：  
  
-   匹配的开始标记和结束标记。  
  
-   任何“\<”或“\>”尖括号对。  
  
-   注释的开始和结束。  
  
-   处理指令的开始和结束。  
  
-   CDATA 块的开始和结束。  
  
-   DTD 声明的开始和结束。  
  
-   特性的左引号和右引号。  
  
## 修改智能感知选项  
 默认情况下启用智能感知和自动完成功能。但是，可以通过修改“工具\-选项”设置来更改此选项。  
  
 “杂项”页的“自动插入”部分控制以下行为：  
  
|名称|说明|  
|--------|--------|  
|结束标记|为新元素插入结束标记。|  
|特性引号|在输入新特性名时插入特性值引号。|  
|其他标记|完成注释、CDATA、DOCTYPE、处理指令和其他标记声明。|  
  
#### 更改自动完成行为  
  
1.  从“工具”菜单中选择“选项”。  
  
2.  展开“文本编辑器”，展开“XML”，再选择“杂项”。  
  
3.  对“自动插入”部分进行所需的更改，再单击“确定”。  
  
## 请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)   
 [使用 IntelliSense](../ide/using-intellisense.md)   
 [演练：使用 XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)