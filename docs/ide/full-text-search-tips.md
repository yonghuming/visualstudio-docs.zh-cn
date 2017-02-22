---
title: "全文搜索提示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_search"
helpviewer_keywords: 
  - "Help Viewer 2.0, 全文搜索提示"
  - "全文搜索提示 [Help Viewer 2.0]"
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 全文搜索提示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在帮助中查找信息的最有用的一个方法是执行全文搜索。  若要优化和自定义您的结果，您必须了解语法如何影响您的查询。  本主题提供提示、过程和详细语法信息帮助您更好地构思您的查询。  
  
## 全文搜索提示  
 如果您理解“帮助”怎样解释您在查询中使用的格式，您可以创建只返回使您感兴趣的这些主题的更多的目标搜索。  这些格式包括特殊字符、保留字和筛选器。  
  
### 通用准则  
 下表包含“帮助”开发搜索查询的基本规则和指南。  
  
|语法|说明|  
|--------|--------|  
|区分大小写|搜索不区分大小写。  使用大写或小写字母，开发您的搜索条件。  例如，“OLE”和“ole”返回相同的结果。|  
|字符组合|您不能只搜索单个字母 \(a–z\) 或单个数字 \(0–9\)。  如果尝试搜索某些保留字，如“and”， “from”和“with”，则它们将被忽略。  有关更多信息，请参见本主题“在搜索后忽略的字符串\(停止运行\)”。|  
|计算顺序|搜索查询都是从左到右进行求值。|  
  
### 搜索语法  
 如果指定由多个单词组成的搜索字符串，如“单词1 单词2，”，该字符串的搜索字符串与键入“单词1和单词2”等效，仅返回搜索字符串中包含的所有单词的主题。  
  
> [!IMPORTANT]
>  1.  不受支持的短语搜索。  如果在搜索字符串指定多个符，返回的主题将包含您指定的所有单词但并不是精确到指定的具体的词。  
> 2.  使用逻辑运算符指定您搜索短语中单词之间的关系。  您可以包括 AND、OR、NOT 和 NEAR 等逻辑运算符来进一步优化您的搜索。  例如，如果搜索“declaring NEAR union”，搜索结果中的主题将包含单词“declaring”和“union”不超过彼此的几个词。  有关更多信息，请参见 [搜索表达式中的逻辑运算符](../ide/logical-operators-in-search-expressions.md)。  
  
### 筛选器  
 您可以通过使用高级的搜索运算符进一步限制搜索结果。  帮助包含可用于筛选全文搜索结果的三个类别:标题、代码和关键字。  有关更多信息，请参见 [搜索表达式中的高级搜索运算符](../ide/advanced-search-operators-in-search-expressions.md)。  
  
### 对搜索结果进行分级  
 搜索算法适用于特定条件的标准以帮助排名搜索结果或结果列表中的低。  一般情况下:  
  
1.  内容中标题包含搜索字词的部分级别要高于标题不包含搜索字词的内容。  
  
2.  内容中的几乎接近搜索字词的部分级别要高于不接近搜索字词的内容。  
  
3.  内容包含的高密度搜索字词级别高于低密度搜索字词的的内容排列。  
  
### “在搜索中忽略的单词（停止词）”  
 常出现的单词或数字，有时称为停止词，在全文搜索过程中会被自动忽略。  例如，如果要搜索短语“pass through”，搜索结果将显示都包含单词“pass”的主题，而不会包含“through”。  
  
## 请参阅  
 [找到信息](../ide/locate-information.md)   
 [搜索表达式中的逻辑运算符](../ide/logical-operators-in-search-expressions.md)