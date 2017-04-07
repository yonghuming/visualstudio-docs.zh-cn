---
title: "类设计器中的 Visual C++ 枚举 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 168e14b8f7e913a2dc4656f01f8cc5cc8ff80284
ms.lasthandoff: 04/05/2017

---
# <a name="visual-c-enumerations-in-class-designer"></a>类设计器中的 Visual C++ 枚举
类设计器支持 C++ `enum` 和范围 `enum class` 类型。 下面是一个示例：  
  
```  
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
```  
  
 类图中的 C++ 枚举形状的外观和工作原理与结构形状类似，只不过其标签显示为 **Enum** 或 **Enum class**，标签的颜色为粉色而不是蓝色，并且具有带颜色的边框左边和上边。 两种枚举形状和结构形状都具有方角。  
  
 有关使用 `enum` 类型的更多信息，请参阅[枚举](/cpp/cpp/enumerations-cpp)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Visual C++ 代码（类设计器）](../ide/working-with-visual-cpp-code-class-designer.md)   
 [枚举](/cpp/cpp/enumerations-cpp)
