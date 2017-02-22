---
title: "CA1704：标识符应正确拼写 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1704：标识符应正确拼写
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 标识符的名称中包含一个或多个 Microsoft 拼写检查器库不能识别的单词。  此规则不检查构造函数或具有特殊名称的成员，例如 get 和 set 属性访问器。  
  
## 规则说明  
 此规则将标识符解析为标记并检查每个标记的拼写。  解析算法执行下列转换：  
  
-   一个新标记以大写字母开头。  例如，MyNameIsJoe 被解析为“My”、“Name”、“Is”和“Joe”标记。  
  
-   对于多个大写字母，最后一个大写字母开始一个新标记。  例如，GUIEditor 被解析为“GUI”和“Editor”标记。  
  
-   移除前导和尾随撇号。  例如，“'sender'”被解析为“sender”标记。  
  
-   下划线表示一个标记的结尾，并被移除。  例如，Hello\_world 被解析为“Hello”和“world”标记。  
  
-   嵌入的与号将被移除。  例如，for&mat 被解析为“format”标记。  
  
 默认情况下，使用拼写检查器的英语 \(en\) 版本。  目前没有其他语言字典。  
  
## 如何解决冲突  
 若要修复与此规则的冲突，请更正单词的拼写，或者将单词添加到名为 CustomDictionary.xml 的自定义字典中。  将该字典放在工具的安装目录、项目目录或者用户配置文件下与该工具关联的目录 \(%USERPROFILE%\\Application Data\\...\) 中。  若要了解如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中将自定义词典添加到项目，请参阅[如何：自定义代码分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)。  
  
-   将不应造成冲突的单词添加到 Dictionary\/Words\/Recognized 路径下。  
  
-   将应造成冲突的单词添加到 Dictionary\/Words\/Unrecognized 路径下。  
  
-   将应标记为已过时的单词添加到 Dictionary\/Words\/Deprecated 路径下。  有关更多信息，请参见相关的规则主题[CA1726：使用首选词条](../code-quality/ca1726-use-preferred-terms.md)。  
  
-   将首字母缩写词大小写规则的异常添加到 Dictionary\/Acronyms\/CasingExceptions 路径下。  
  
 下面是自定义字典文件的结构示例。  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## 何时禁止显示警告  
 只有当单词是故意拼写错误并且单词适用于有限的库集合时，才可以禁止显示此规则发出的警告。  拼写正确的单词可以减少新软件库所需的学习曲线。  
  
## 相关规则  
 [CA2204：应正确拼写文本](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703：资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：标识符不应包含下划线](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726：使用首选词条](../code-quality/ca1726-use-preferred-terms.md)  
  
## 请参阅  
 [如何：自定义代码分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)