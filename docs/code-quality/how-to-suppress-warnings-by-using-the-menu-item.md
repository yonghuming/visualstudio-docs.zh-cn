---
title: "如何： 使用菜单项禁止显示警告 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a197170285a8f8a9d3f0cc01638557f30fd1f126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>如何：使用菜单项禁止显示警告
> [!NOTE]
>  在源代码中，不支持对网站项目进行禁止显示操作。  
  
 您可以使用“代码分析”窗口来禁止显示代码分析警告。 禁止显示警告与禁用不同。 禁止显示警告时，它仅适用于冲突的特定实例。 在错误列表窗口中仍会报告相同的警告的其他冲突。  
  
 在运行代码分析之后，您可能会确定“代码分析”窗口中显示的一条或多条代码分析警告不适用于您的应用程序。 例如，可能会确定代码正确。 或者，它可能会出现这种情况，某些冲突较低的优先级，将不在当前的开发周期中修复。 无论是什么原因，它会经常用到指示的警告就是不适用以便你团队成员就会知道已评审过代码并且已确定无法禁止显示警告。 在源代码中，禁止显示功能很有用，因为它可以让您将禁止显示功能放在生成警告的位置附近。  
  
 你可以选择是否禁止显示就会显示在源代码中或在全局禁止显示文件中。 必须在全局禁止显示文件中放置某些禁止显示功能。 如果出现这种情况，**在源**选项将被禁用。  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>若要通过使用菜单项禁止显示警告  
  
1.  上**分析**菜单上，选择**Windows** ，然后选择**代码分析**。  
  
2.  在**代码分析**窗口中，选择警告禁止显示。  
  
3.  选择操作，然后选择**禁止显示消息**，然后选择**在源**或**在项目禁止显示文件**。  
  
     特定警告将被禁止显示，并且带着删除线显示在“代码分析”窗口中。  
  
> [!NOTE]
>  不具有目标的禁止显示出现在全局禁止显示文件。