---
title: "演练：创建支持简单数据绑定的 Windows 窗体用户控件 | Microsoft Docs"
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
  - "自定义控件 [Visual Studio], “数据源”窗口"
  - "“数据源”窗口, 控件"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建支持简单数据绑定的 Windows 窗体用户控件
在 Windows 应用程序的窗体上显示数据时，你可以从**“工具箱”**中选择现有的控件，而当标准控件无法提供应用程序所要求的功能时，你还可以创作自定义控件。  本演练显示了如何创建实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控件。  用于实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控件可以包含一个可以绑定到数据的属性。  此类控件类似于 <xref:System.Windows.Forms.TextBox> 或 <xref:System.Windows.Forms.CheckBox>。  
  
 有关控件创作的详细信息，请参阅[设计时开发 Windows 窗体控件](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)。  
  
 创作用于数据绑定方案中的控件时，你需要实现以下数据绑定特性之一：  
  
|数据绑定特性的用法|  
|---------------|  
|在简单控件上实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>（如 <xref:System.Windows.Forms.TextBox>），此类控件用于显示数据的单个列（或属性）。  （本演练页面描述了此过程）。|  
|在控件上实现 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>（如 <xref:System.Windows.Forms.DataGridView>），此类控件用于显示数据列表（或表）。  有关详细信息，请参阅[演练：创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|  
|在控件上实现 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>（如 <xref:System.Windows.Forms.ComboBox>），此类控件用于显示数据列表（或表），也需要显示数据的单个列或属性。  有关详细信息，请参阅[演练：创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|  
  
 本演练创建了一个简单控件，用于显示表中单个列的数据。  此示例使用 Northwind 示例数据库的 `Customers` 表中的 `Phone` 列。  通过使用 <xref:System.Windows.Forms.MaskedTextBox> 并设置电话号码的掩码，该简单的用户控件可以标准的电话号码格式显示客户的电话号码。  
  
 在本演练中，你将学会如何执行以下任务：  
  
-   创建新的**“Windows 应用程序”**。  
  
-   将新的**“用户控件”**添加到你的项目中。  
  
-   以可视方式设计用户控件。  
  
-   实现 `DefaultBindingProperty` 特性。  
  
-   使用[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)创建数据集。  
  
-   在**“数据源”**窗口中，设置**“电话”**列，以使用新的控件。  
  
-   创建一个用于在新控件中显示数据的窗体。  
  
## 系统必备  
 若要完成本演练，你将需要：  
  
-   能够访问 Northwind 示例数据库。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建 Windows 应用程序  
 第一步是创建**“Windows 应用程序”**。  
  
#### 创建新的 Windows 项目  
  
1.  在 Visual Studio 中，从**“文件”**菜单创建一个新的**“项目”**。  
  
2.  将项目命名为 **SimpleControlWalkthrough**。  
  
3.  选择**“Windows 应用程序”**，然后单击**“确定”**。  有关详细信息，请参阅[客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     **“SimpleControlWalkthrough”**项目即被创建并添加到**“解决方案资源管理器”**中。  
  
## 将用户控件添加到项目中  
 本演练通过**“用户控件”**创建一个简单的可绑定数据控件，以便将**“用户控件”**项添加到**“SimpleControlWalkthrough”**项目中。  
  
#### 将用户控件添加到项目中  
  
1.  从**“项目”**菜单中，选择**“添加用户控件”**。  
  
2.  在名称区域中键入 `PhoneNumberBox`，然后单击**“添加”**。  
  
     **“PhoneNumberBox”**控件将会添加到**“解决方案资源管理器”**中，并在设计器中打开。  
  
## 设计 PhoneNumberBox 控件  
 本演练对现有 <xref:System.Windows.Forms.MaskedTextBox> 进行了扩展，以创建 `PhoneNumberBox` 控件。  
  
#### 设计 PhoneNumberBox 控件  
  
1.  将 <xref:System.Windows.Forms.MaskedTextBox> 从**“工具箱”**拖到该用户控件的设计图面上。  
  
2.  选择刚刚拖动的 <xref:System.Windows.Forms.MaskedTextBox> 上的智能标记，然后选择**“设置掩码”**。  
  
3.  在**“输入掩码”**对话框中选择**“电话号码”**，然后单击**“确定”**以设置掩码。  
  
## 添加所需的数据绑定特性  
 对于支持数据绑定的简单控件，应实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>。  
  
#### 实现 DefaultBindingProperty 特性  
  
1.  将 `PhoneNumberBox` 控件切换到代码视图。  （在**“视图”**菜单上，选择**“代码”**。）  
  
2.  将 `PhoneNumberBox` 中的代码替换为以下内容：  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  从**“生成”**菜单中选择**“生成解决方案”**。  
  
## 从数据库创建数据源  
 此步骤根据 Northwind 示例数据库中的 `Customers` 表，使用**“数据源配置向导”**创建数据源。  你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。  有关设置 Northwind 示例数据库的信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
#### 创建数据源  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
2.  在**“数据源”**窗口中，选择**“添加新数据源”**以启动**“数据源配置向导”**。  
  
3.  在**“选择数据源类型”**页上选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择你的数据连接”**页面上，执行以下操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         Or  
  
    -   选择**“新建连接”**，以启动**“添加\/修改连接”**对话框。  
  
5.  如果数据库需要密码，请选择该选项以包括敏感数据，再单击**“下一步”**。  
  
6.  在**“将连接字符串保存到应用程序配置文件”**页面上单击**“下一步”**。  
  
7.  在**“选择数据库对象”**页面上展开**“表”**节点。  
  
8.  选择 `Customers` 表，然后单击**“完成”**。  
  
     **“NorthwindDataSet”**即被添加到你的项目中，并且**“数据源”**窗口中将显示 `Customers` 表。  
  
## 将“电话”列设置为使用“PhoneNumberBox”控件  
 在**“数据源”**窗口中，你可以先设置要创建的控件，然后再将项拖动到窗体上。  
  
#### 将“电话”列设置为绑定到“PhoneNumberBox”控件  
  
1.  在设计器中打开**“Form1”**。  
  
2.  在**“数据源”**窗口中展开**“Customers”**节点。  
  
3.  在**“Customers”**节点上单击下拉箭头，然后从控件列表中选择**“详细信息”**。  
  
4.  单击**“电话”**列上的下拉箭头，然后选择**“自定义”**。  
  
5.  从**“数据 UI 自定义选项”**对话框中的**“关联的控件”**列表中，选择**“PhoneNumberBox”**。  
  
6.  单击**“电话”**列上的下拉箭头，然后选择**“PhoneNumberBox”**。  
  
## 将控件添加到窗体  
 通过将**“数据源”**窗口中的项拖到窗体上，可创建数据绑定控件。  
  
#### 在窗体上创建数据绑定控件  
  
-   将主**“Customers”**节点从**“数据源”**窗口拖到窗体上，然后验证是否将 `PhoneNumberBox` 控件用于显示 `Phone` 列中的数据。  
  
     带有描述性标签的数据绑定控件将显示在窗体上，同时还显示一个工具条 \(<xref:System.Windows.Forms.BindingNavigator>\)，用于在记录间进行导航。  组件栏中出现 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
## 运行应用程序  
  
#### 运行应用程序  
  
-   按 F5 运行该应用程序。  
  
## 后续步骤  
 根据应用程序的要求，在创建了支持数据绑定的控件后，可能还需要执行一些步骤。  接下来的一些常见步骤包括：  
  
-   将你的自定义控件置于控件库中，以便在其他应用程序中重用它们。  
  
-   创建支持更复杂的数据绑定方案的控件。  有关详细信息，请参阅[演练：创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)和[演练：创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。  
  
## 请参阅  
 [设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)