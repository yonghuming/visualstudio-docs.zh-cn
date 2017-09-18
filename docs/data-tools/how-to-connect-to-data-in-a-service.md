---
title: "如何：连接到服务中的数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], 连接到 Web 服务"
  - "数据 [Visual Studio], 从 Web 服务读取"
  - "数据源, 从 Web 服务创建"
  - "读取数据, 从 Web 服务"
  - "Web 服务, 作为数据源"
  - "Web 服务, 连接"
  - "Web 服务, 读取数据"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：连接到服务中的数据
通过运行[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)并在**“选择数据源类型”**页上选择**“服务”**，可将应用程序连接到服务所返回的数据。  
  
 该向导完成后，将会向项目中添加一个服务引用，且此引用在[“数据源”窗口](../Topic/Data%20Sources%20Window.md)中立即可用。  
  
> [!NOTE]
>  **“数据源”**窗口中显示的项取决于服务返回的信息。  某些服务可能没有为**“数据源配置向导”**创建可绑定的对象提供足够的信息。  例如，如果服务返回一个非类型化数据集，则向导完成时**“数据源”**窗口中将不会出现任何项。  这是因为非类型化数据集不提供架构，所以该向导没有足够的信息来创建数据源。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 将应用程序连接到服务  
  
1.  在**“数据”**菜单上，单击**“添加新数据源”**。  
  
2.  在**“选择数据源类型”**页上选择**“服务”**，然后单击**“下一步”**。  
  
3.  输入要使用的服务的地址，或单击**“发现”**找到当前解决方案中的服务，然后单击**“前往”**。  
  
4.  （可选）可以键入一个新的**“命名空间”**来替代默认值。  
  
    > [!NOTE]
    >  单击**“高级”**打开[“配置服务引用”对话框](../data-tools/configure-service-reference-dialog-box.md)。  
  
5.  单击**“确定”**以将服务引用添加到项目。  
  
6.  单击**“完成”**。  
  
     该数据源将被添加到**“数据源”**窗口中。  
  
## 后续步骤  
  
#### 在应用程序中添加功能  
  
-   在**“数据源”**窗口中选择一个项并将其拖动到一个窗体上，从而创建绑定控件。  有关更多信息，请参见[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## 请参阅  
 [演练：将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [演练：将 Silverlight 控件绑定到 WCF 数据服务](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)