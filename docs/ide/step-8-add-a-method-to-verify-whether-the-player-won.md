---
title: "步骤 8：添加方法以验证玩家是否获胜 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 步骤 8：添加方法以验证玩家是否获胜
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

你已创建了一个有趣的游戏，但需要添加其他项来完成制作。  该游戏应当在玩家获胜时结束，因此你需要添加 `CheckForWinner()` 方法以验证玩家是否获胜。  
  
### 添加方法以验证玩家是否获胜  
  
1.  在你的代码底部，`CheckForWinner()` 事件处理程序下方添加一个 `timer1_Tick()` 方法，如以下代码所示。  
  
     [!code-cs[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]  
  
     该方法使用 `foreach` 循环（Visual C\# 中）或 `For Each` 循环（Visual Basic 中）遍历 TableLayoutPanel 中的每个标签。  它使用相等运算符（在 Visual C\# 中为 `==`，在 Visual Basic 中为 `=`）检查每个标签的图标颜色以验证它是否与背景匹配。  如果颜色匹配，图标将保持不可见，玩家还没有匹配所有剩余的图标。  在这种情况下，程序使用 `return` 语句跳过其余方法。  如果循环遍历所有标签而不执行 `return` 语句，则意味着窗体上的所有图标均已匹配。  该程序将显示一个恭喜玩家获胜的 MessageBox，然后调用窗体的 `Close()` 方法来结束游戏。  
  
2.  接下来，让标签的 Click 事件处理程序调用新的 `CheckForWinner()` 方法。  请确保程序在显示玩家选择的第二个图标后立即检查是否有赢家。  查找设置第二个选中图标颜色的行，然后在其后直接调用 `CheckForWinner()` 方法，如以下代码所示。  
  
     [!code-cs[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]  
  
3.  保存并运行程序。  玩游戏并匹配所有图标。  当你获胜时，该程序将显示一个祝贺性的 MessageBox（如下图所示），然后关闭该框。  
  
     ![具有 MessageBox 的匹配游戏](../ide/media/express_tut4step8.png "Express\_Tut4Step8")  
具有 MessageBox 的匹配游戏  
  
### 继续或查看  
  
-   若要转到下一个教程步骤，请参阅[步骤 9：尝试其他功能](../ide/step-9-try-other-features.md)。  
  
-   若要返回上一个教程步骤，请参阅[步骤 7：保持对可见](../Topic/Step%207:%20Keep%20Pairs%20Visible.md)。