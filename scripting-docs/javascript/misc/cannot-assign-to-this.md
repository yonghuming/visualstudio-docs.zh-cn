---
title: "无法分配到 &#39; 这 &#39; |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>无法分配到 &#39; 这 &#39;
你试图将值赋给**这**。 **这**是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引用以下任一项的关键字：  
  
-   当前正在执行的一种方法，该对象  
  
-   如果没有当前方法 （或该方法不属于任何其他对象） 的全局对象。  
  
 一种方法是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]通过对象调用的函数。 在方法中，**这**关键字是对通过调用该方法的对象的引用 (这碰巧是通过调用带的类构造函数创建的对象**新**运算符)。  
  
 在方法中，你可以使用**这**来引用当前对象，但你无法将新值赋给**这**。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   请不要尝试将分配给**这**。 若要访问的属性或方法实例化对象，使用点运算符 (例如，circle**。**半径）。  
  
    > [!NOTE]
    >  不能将命名的用户创建的变量**这**; 它是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]保留字。  
  
## <a name="see-also"></a>另请参阅  
 [此语句](../../javascript/reference/this-statement-javascript.md)   
 [脚本疑难解答](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)