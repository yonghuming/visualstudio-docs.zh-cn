---
title: "将控件绑定到图片中，从数据库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bc71529f852e87ca206509e06cb80940c11ac36d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="bind-controls-to-pictures-from-a-database"></a>将控件绑定到图片中，从数据库
你可以使用**数据源**窗口将在数据库中的图像绑定到你的应用程序中的控件。 例如，你可以将图像绑定到<xref:System.Windows.Controls.Image>控制在 WPF 应用程序，或为<xref:System.Windows.Forms.PictureBox>在 Windows 窗体应用程序中的控件。  
  
字节数组形式通常存储在数据库中的图片。 中的项**数据源**将存储为字节数组具有键入其控件的窗口将设置为**无**默认情况下，由于字节数组可能包含一个简单的可执行文件的字节数组中的任何内容大型应用程序。 若要创建数据绑定控件中的字节数组项**数据源**表示的图像的窗口，你必须选择要创建的控件。  
  
以下过程假设**数据源**窗口已填入项绑定到你的映像。 
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>若要将数据库中的图片绑定到控件  
  
1.  请确保你想要将控件添加到设计图面是在 WPF 设计器或 Windows 窗体设计器中打开。  
  
2.  在**数据源**窗口中，展开所需的表或对象以显示其列或属性。  
  
3.  选择的列或属性包含映像数据，并从其下拉控件列表中选择以下控件之一：  
  
    -   如果 WPF 设计器打开，请选择**映像**。  
  
    -   Windows 窗体设计器处于打开状态，如果选择**PictureBox**。  
  
    -   或者，你可以选择一个不同的控件的支持数据绑定，可显示图像。 如果你想要使用的控件不在的可用控件列表中，你可以将其添加到列表，然后选择它。 有关详细信息，请参阅[将自定义控件添加到数据源窗口](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
## <a name="see-also"></a>请参阅
[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)