---
title: "如何： 将自定义任务窗格添加到应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1a39267da04be68793a2236250e5ed10efb01afd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>如何：向应用程序中添加自定义任务窗格
  你可以通过使用 VSTO 外接程序向上面列出的应用程序添加自定义任务窗格。 有关详细信息，请参阅[自定义任务窗格](../vsto/custom-task-panes.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="adding-a-custom-task-pane-to-an-application"></a>向应用程序添加自定义任务窗格  
  
#### <a name="to-add-a-custom-task-pane-to-an-application"></a>若要向应用程序添加自定义任务窗格  
  
1.  为上面列出的应用程序之一打开或创建 VSTO 外接程序项目。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 **“项目”** 菜单上，单击 **“添加用户控件”**。  
  
3.  在**添加新项**对话框框中，更改到新的用户控件的名称**MyUserControl**，然后单击**添加**。  
  
     用户控件将在设计器中打开。  
  
4.  添加一个或多个 Windows 窗体控件从**工具箱**到用户控件。  
  
5.  打开**ThisAddIn.cs**或**ThisAddIn.vb**代码文件。  
  
6.  向 `ThisAddIn` 类添加下面的代码。 此代码将 `MyUserControl` 和 <xref:Microsoft.Office.Tools.CustomTaskPane> 的实例声明为 `ThisAddIn` 类的成员。  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  将以下代码添加到 `ThisAddIn_Startup` 事件处理程序中。 此代码通过将 `MyUserControl` 对象添加到 `CustomTaskPanes` 集合来创建新 <xref:Microsoft.Office.Tools.CustomTaskPane>。 代码还将显示任务窗格。  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  此代码将自定义任务窗格与应用程序中的活动窗口关联。 对于某些应用程序，你可能想要修改此代码以确保任务窗格与应用程序中的其他文档或项目一起显示。 有关详细信息，请参阅[自定义任务窗格](../vsto/custom-task-panes.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Office UI 自定义项](../vsto/office-ui-customization.md)   
 [自定义任务窗格](../vsto/custom-task-panes.md)   
 [演练：从自定义任务窗格自动化应用程序](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  