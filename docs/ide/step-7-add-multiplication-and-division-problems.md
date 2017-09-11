---
title: "步骤 7：添加乘法和除法问题 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 17
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
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 481d1ad8050a0b028a7cbf23f9385c9920feb1a2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="step-7-add-multiplication-and-division-problems"></a>步骤 7：添加乘法和除法问题
在本教程的第 7 部分中，您将添加乘法和除法题，但首先要考虑如何做出这种更改。 考虑与存储值相关的初始步骤。  
  
### <a name="to-add-multiplication-and-division-problems"></a>添加乘法和除法问题  
  
1.  再向窗体添加四个整型变量。  
  
     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]  [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  
  
2.  与前面的操作一样，修改 `StartTheQuiz()` 方法，以便为乘法和除法题填入随机数。  
  
     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]  [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  
  
3.  修改 `CheckTheAnswer()` 方法，使之同样检查乘法和除法题。  
  
     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]  [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  
  
     由于使用键盘无法方便地输入乘号 (×) 和除号 (÷)，因此 Visual C# 和 Visual Basic 接受用星号 (*) 代替乘号，用斜线 (/) 代替除号。  
  
4.  更改计时器 Tick 事件处理程序的最后部分，使其在时间用完时填入正确答案。  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]  [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  
  
5.  保存并运行程序。  
  
     如下图所示，测验对象必须回答四个问题才能完成测验。  
  
     ![包含四个问题的数学测验](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
包含四个问题的数学测验  
  
### <a name="to-continue-or-review"></a>继续或查看  
  
-   若要转到下一个教程，请参阅[步骤 8：自定义测验](../ide/step-8-customize-the-quiz.md)。  
  
-   若要返回上一个教程，请参阅[步骤 6：添加减法问题](../ide/step-6-add-a-subtraction-problem.md)。
