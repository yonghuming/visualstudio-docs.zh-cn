---
title: 'Step 7: Add Multiplication and Division Problems | Microsoft Docs'
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
ms.lasthandoff: 08/30/2017

---
# <a name="step-7-add-multiplication-and-division-problems"></a>Step 7: Add Multiplication and Division Problems
In the seventh part of this tutorial, you'll add multiplication and division problems, but first think about how to make that change. Consider the initial step, which involves storing values.  
  
### <a name="to-add-multiplication-and-division-problems"></a>To add multiplication and division problems  
  
1.  Add four more integer variables to the form.  
  
     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]  [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  
  
2.  As you did before, modify the `StartTheQuiz()` method to fill in random numbers for the multiplication and division problems.  
  
     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]  [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  
  
3.  Modify the `CheckTheAnswer()` method so that it also checks the multiplication and division problems.  
  
     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]  [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  
  
     You can't easily enter the multiplication sign (×) and the division sign (÷) using the keyboard, so Visual C# and Visual Basic accept an asterisk (*) for multiplication and a slash mark (/) for division.  
  
4.  Change the last part of the timer's Tick event handler so that it fills in the correct answer when time runs out.  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]  [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  
  
5.  Save and run your program.  
  
     Quiz takers must answer four problems to complete the quiz, as the following illustration shows.  
  
     ![Math quiz with four problems](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Math quiz with four problems  
  
### <a name="to-continue-or-review"></a>To continue or review  
  
-   To go to the next tutorial step, see [Step 8: Customize the Quiz](../ide/step-8-customize-the-quiz.md).  
  
-   To return to the previous tutorial step, see [Step 6: Add a Subtraction Problem](../ide/step-6-add-a-subtraction-problem.md).