---
title: "如何： 自定义代码分析字典 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a14870e494c9c8efeb7c15dabf034f059c4a3c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>如何：自定义代码分析字典
代码分析使用内置的字典来检查拼写，语法情况下和的其他命名约定中的错误代码中的标识符[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]准则。 你可以创建要添加、 删除或修改条款、 缩写，以及对内置字典首字母缩写词的自定义字典 Xml 文件。  
  
 例如，假设你的代码包含一个名为类**DoorKnokker**。 代码分析将作为两个单词的复合标识的名称：**门**和**knokker**。 然后，它将引发警告的**knokker**拼写不正确。 若要强制代码分析，以识别拼写是否正确，你可以添加字词**knokker**到自定义的字典。  
  
## <a name="to-create-a-custom-dictionary"></a>若要创建自定义字典  
 创建名为的文件**CustomDictionary.xml**。  
  
 使用以下 XML 结构定义您自定义的语言：  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## <a name="custom-dictionary-elements"></a>自定义词典元素  
 可以通过添加作为自定义字典中的以下元素的内部文本的条款来修改代码分析字典中的行为：  
  
-   [字典/单词/识别/中的单词](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [字典/单词/无法识别的/中的单词](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [字典/单词/弃用/术语 [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [字典/单词/复合/术语 [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [字典/单词/DiscreteExceptions/术语](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [字典/首字母缩写词/CasingExceptions/首字母缩写词](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a>字典/单词/识别/中的单词  
 若要在代码分析标识正确地拼写的术语的列表中包含一个术语，请为字典/单词/识别/Word 元素内部文本添加术语。 字典/单词/识别/Word 元素中的条款不区分大小写。  
  
 **示例**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 字典/单词/识别节点中的条款将应用到下面的代码分析规则：  
  
-   [CA1701：资源字符串复合词应采用正确的大小写](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：复合词应采用正确的大小写](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726：使用首选词条](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204：应正确拼写文本](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>字典/单词/无法识别的/中的单词  
 若要从代码分析标识正确地拼写的术语的列表中排除一个术语，添加条件以排除字典/单词/无法识别/Word 元素的内部文本。 字典/单词/无法识别/Word 元素中的条款不区分大小写。  
  
 **示例**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 无法识别的单词/字典/节点中的条款将应用到下面的代码分析规则：  
  
-   [CA1701：资源字符串复合词应采用正确的大小写](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：复合词应采用正确的大小写](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726：使用首选词条](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204：应正确拼写文本](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>字典/单词/弃用/术语 [@PreferredAlternate]  
 若要在代码分析标识为不推荐使用的术语的列表中包含一个术语，请为字典/单词/已弃用/术语元素内部文本添加术语。 不推荐使用的术语是一个字的拼写正确，但不应使用。  
  
 若要在警告中包含建议的替代字词，字词元素 PreferredAlternate 特性中指定备用服务器。 如果你不想要建议替代方法，可以将属性值留空。  
  
-   字典/字不推荐使用的术语/已弃用/术语元素不区分大小写。  
  
-   PreferredAlternate 属性值是区分大小写。 复合的替代项为使用 Pascal 大小写。  
  
 **示例**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 已弃用字典/单词节点中的条款将应用到下面的代码分析规则：  
  
-   [CA1701：资源字符串复合词应采用正确的大小写](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：复合词应采用正确的大小写](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726：使用首选词条](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>字典/单词/复合/术语 [@CompoundAlternate]  
 内置字典标识为单个、 离散的词，而不是为复合字词的一些术语。 若要在代码分析的组合词作为标识的术语的列表中包括一个术语，并指定术语的正确大小写，字典/单词/复合/术语元素内部文本的形式添加字词。 在术语元素 CompoundAlternate 属性中，指定利用不同的单词 （Pascal 大小写） 的第一个字母组成的复合术语的各单词。 请注意，则内部文本中指定的术语自动添加到字典/单词/DiscreteExceptions 列表。  
  
-   字典/字不推荐使用的术语/已弃用/术语元素不区分大小写。  
  
-   PreferredAlternate 属性值是区分大小写。 复合的替代项为使用 Pascal 大小写。  
  
 **示例**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 字典/单词/复合节点中的条款将应用到下面的代码分析规则：  
  
-   [CA1701：资源字符串复合词应采用正确的大小写](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：复合词应采用正确的大小写](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>字典/单词/DiscreteExceptions/术语  
 若要排除的代码分析标识为单个的字词列表中的字词，离散 word 时由复合词的大小写规则检查术语字典/单词/DiscreteExceptions/术语元素内部文本的形式添加字词。 字典/单词/DiscreteExceptions/术语元素中的术语不区分大小写。  
  
 **示例**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 字典/单词/DiscreteExceptions 节点中的条款将应用到下面的代码分析规则：  
  
-   [CA1701：资源字符串复合词应采用正确的大小写](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：复合词应采用正确的大小写](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>字典/首字母缩写词/CasingExceptions/首字母缩写词  
 若要包括的代码分析标识为拼写正确的术语列表中的首字母缩写词并指示时由大小写检查术语的首字母缩写的规则的复合词，字典/首字母缩写词/CasingExceptions 内部文本的形式添加字词 /Acronym 元素。 字典/首字母缩写词/CasingExceptions/首字母缩写词元素中的首字母缩写是区分大小写。  
  
 **示例**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 字典/首字母缩写词/CasingExceptions 节点中的条款将应用到下面的代码分析规则：  
  
-   [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>若要应用于项目的自定义字典  
  
1.  在**解决方案资源管理器**，使用以下过程之一：  
  
2.  要将一个字典添加到单个项目中，右键单击项目名称，然后单击**添加现有项**。 指定的文件中**添加现有项**对话框。  
  
3.  若要添加一个字典，其中两个或多个项目之间共享，找到要在共享的文件**添加现有项**对话框框中，单击向下箭头**添加**按钮，然后单击**添加为链接**.  
  
4.  在**解决方案资源管理器**，右键单击**CustomDictionary.xml**文件名称，然后单击**属性**。  
  
5.  从**生成操作**列表中，选择**CodeAnalysisDictionary**。  
  
6.  从**复制到输出目录**列表中，选择**不复制**。