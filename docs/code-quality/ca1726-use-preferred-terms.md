---
title: "CA1726： 使用首选的词条 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords: UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ae02d0eb136d45bc2b8af7dde5f897765493050
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1726-use-preferred-terms"></a>CA1726：使用首选词条
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|类别|Microsoft.Naming|  
|是否重大更改|-对程序集引发时中断<br /><br /> 无间断-如果对类型参数引发|  
  
## <a name="cause"></a>原因  
 在外部可见的标识符的名称中，包括一个存在首选备用词条的词条。 或者，名称中包含标志或标志一词。  
  
## <a name="rule-description"></a>规则说明  
 此规则将标识符分析为标记。 每个单个标记和每个连续的双标记组合到内置到规则和任何自定义词典已弃用部分中的条款进行比较。 下表演示已内置到规则以及其首选备用词条的词条。  
  
|过时的术语|首选的词条|  
|-------------------|--------------------|  
|不是|上|  
|已取消|Canceled|  
|无法|不能|  
|ComPlus|EnterpriseServices|  
|Couldnt|不能|  
|Didnt|DidNot|  
|无法|不|  
|注意事项|不要|  
|标志或标志|没有任何替换术语。 请勿使用。|  
|未|HadNot|  
|尚未|HasNot|  
|尚未|HaveNot|  
|索引|索引|  
|不是|IsNot|  
|登录名|登录|  
|注销|注销|  
|Shouldnt|ShouldNot|  
|登录|登录|  
|签收|注销|  
|Wasnt|WasNot|  
|没有|未|  
|不|翻译已经不再|  
|Wouldnt|WouldNot|  
|可写|可写|  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将替换为首选备用词条术语。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 仅当标识符的名称是有意的且明确地与原始术语而不是首选的词条相关，禁止显示此规则的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [命名警告](../code-quality/naming-warnings.md)