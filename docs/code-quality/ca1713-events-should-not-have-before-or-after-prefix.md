---
title: "CA1713： 事件应不具有 before 或 after 前缀 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c211d2f2cc65c12fd11782058c5e8b8a3aaf47b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713：事件不应具有 before 或 after 前缀
|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 事件的名称以 Before 或之后开头。  
  
## <a name="rule-description"></a>规则说明  
 事件名称应说明引发事件的操作。 若要命名按特定顺序引发的相关事件，请使用现在时或过去时指示一系列操作中的相对位置。 例如，命名的成对的事件都发出时关闭资源时，你可能会将其关闭和已关闭，而不是 BeforeClose 和 AfterClose。  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这减少了学习曲线，才能使用新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 前缀移除的事件名称，并考虑将名称更改为使用现在时或过去时的谓词。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。