---
title: "第 8 步：自定义测验 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 第 8 步：自定义测验
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本教程中的最后一部分中，您在将测试以下方式去自定义测验和根据您已了解的展开。  例如，请考虑程序如何创建一个答案永不为分数的随机除法问题。  若要了解更多信息，请尝试将`“timeLabel”`控件的颜色更改为其他颜色，并为用户提供提示。  
  
### 自定义布局  
  
-   当用户只剩下 5 秒时间时，通过设置“timeLabel”控件的“BackColor”属性 \(`timeLabel.BackColor = Color.Red;`\) 来使其变为红色。  在完成测验后重置此颜色。  
  
-   通过当用户在某个 NumericUpDown 控件中输入正确答案时播放声音来提示用户。（您需要为每个控件的 ValueChanged `ValueChanged()`事件编写事件处理程序，只要用户更改控件的值，就会触发该事件。）  
  
### 继续或查看  
  
-   若要下载测验的完整版本，请参见[数学测验教程完整示例](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)。  
  
-   若要转到下一个教程，请参见[教程 3：创建匹配游戏](../ide/tutorial-3-create-a-matching-game.md)。  
  
-   若要返回上一个教程步骤，请参见[步骤 7：添加乘法和除法问题](../Topic/Step%207:%20Add%20Multiplication%20and%20Division%20Problems.md)。