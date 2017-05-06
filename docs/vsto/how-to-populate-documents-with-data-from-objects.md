---
title: "如何：用对象中的数据填充文档"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "文档 [Visual Studio 中的 Office 开发]，使用数据填充"
  - "数据 [Visual Studio 中的 Office 开发]，添加到文档"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：用对象中的数据填充文档
  在 Microsoft Office Word 文档级项目中，访问数据对象中的数据与访问 Windows 窗体项目中的数据的方式相同。 使用相同的工具和代码将数据从对象引入解决方案，然后即可使用 Windows 窗体控件来显示该数据。 此外，还可以使用主机控件来显示数据。 主机控件是指 Microsoft Office Word 中借助事件和数据绑定容量进行增强的本地对象。 有关详细信息，请参阅[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 必须完成三个基本步骤才能用对象中的数据填充文档：  
  
-   将控件添加到可以绑定到数据的文档。  
  
-   将数据对象添加到文档中。  
  
-   将数据对象连接到 BindingSource。  
  
## 添加数据对象  
  
#### 若要添加数据对象  
  
-   打开“数据源”窗口并从对象创建数据源。 有关详细信息，请参阅[如何：连接到对象中的数据](http://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b)。  
  
## 将数据对象连接到 BindingSource  
 在文档级项目中，可以在设计时向文档中添加控件并将其绑定到数据。  
  
 在 VSTO 外接程序项目中，可以在运行时创建并绑定控件。  
  
### 文档级项目  
  
##### 若要将数据对象连接到 BindingSource  
  
1.  将所需数据字段从“数据源”窗口拖动到你的文档。 此操作会自动创建一个控件。  
  
2.  在代码中，可以创建为数据源选择的对象类型的实例。  
  
3.  将实例分配给 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 属性。  
  
### 应用程序级项目  
  
##### 若要将数据对象连接到 BindingSource  
  
1.  在代码中，可以创建与数据源关联的对象类型的实例。  
  
2.  创建 <xref:System.Windows.Forms.BindingSource> 的实例。  
  
3.  将数据源实例分配给 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 属性。  
  
4.  将数据源作为数据绑定添加到控件。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [如何：用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：使用宿主控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [连接到 Windows 窗体应用程序中的数据](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 组件概述](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  