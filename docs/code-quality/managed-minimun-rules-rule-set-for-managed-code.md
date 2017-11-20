---
title: "托管最少量规则规则的托管代码设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac5ec4db1fe36d7e92c4f9062f8d0c28bae2263e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>托管最少量规则的规则集托管代码
托管最少量规则侧重于在代码中，包括潜在的安全漏洞、 应用程序崩溃和其他重要的逻辑和设计错误的最关键问题。 应包括在任何自定义规则集中设置为你的项目创建此规则。  
  
|规则|描述|  
|----------|-----------------|  
|[CA1001 具有](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|具有可释放字段的类型应该是可释放的|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空终结器|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|应释放可释放的字段|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|重写 ValueType.Equals 时应重载相等运算符|
