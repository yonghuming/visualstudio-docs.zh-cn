---
title: "工具箱，“数据”选项卡 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱，“数据”选项卡"
  - "“数据”选项卡，工具箱"
  - "数据 [Visual Studio]，工具箱"
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 工具箱，“数据”选项卡
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

显示可以添加到窗体和组件的数据对象。  当创建一个具有关联设计器的项目时将显示**“工具箱”**的**“数据”**选项卡。  默认情况下，**“工具箱”**将出现在 Visual Studio 集成开发环境中；如果需要显示**“工具箱”**，请从**“视图”**菜单中选择**“工具箱”**。  
  
> [!TIP]
>  运行“数据源配置向导”可以自动创建和配置大多数数据项。  有关详细信息，请参阅 [Creating Data Applications with Visual Studio](http://msdn.microsoft.com/zh-cn/28edce21-220a-484c-b461-a75b0232d293)。  
  
## UI 元素列表  
 若要直接转到某一组件的 .NET Framework 参考页，请针对**“工具箱”**中的项或设计器栏中的组件项按**“F1”**键。  
  
|名称|描述|  
|--------|--------|  
|<xref:System.Data.DataSet>|向窗体或组件中添加类型化或非类型化数据集的实例。  将该对象拖到设计器上后，它将显示一个对话框，该对话框允许您选择一个现有的类型化数据集类或指定希望创建新的并且空的非类型化数据集。 **Note:**  不要使用**“工具箱”**上的 <xref:System.Data.DataSet> 对象创建新的类型化数据集架构和类。  有关详细信息，请参阅 [如何：创建类型化数据集](../../data-tools/create-and-configure-datasets-in-visual-studio.md)。|  
|<xref:System.Windows.Forms.DataGridView>|提供一种强大而灵活的以表格形式显示数据的方式。|  
|<xref:System.Windows.Forms.BindingSource>|简化了将控件绑定到基础数据源的过程。|  
|<xref:System.Windows.Forms.BindingNavigator>|表示窗体上绑定到数据的控件的导航和操作用户界面 \(UI\)。|  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 的数据应用程序概述](../../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../../data-tools/saving-data.md)