---
title: "创建用户控件支持简单数据绑定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 5f8638a915abe222e5676e0f1aed5134ae00a8e4
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>创建 Windows 窗体用户控件支持简单数据绑定
当在 Windows 应用程序中的窗体上显示数据，你可以选择从现有控件**工具箱**，或如果你的应用程序需要在标准控件中不可用的功能，还可以创作自定义控件。 本演练显示了如何创建实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控件。 用于实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控件可以包含一个可以绑定到数据的属性。 此类控件类似于 <xref:System.Windows.Forms.TextBox> 或 <xref:System.Windows.Forms.CheckBox>。  
  
 有关控件创作的详细信息，请参阅[在设计时开发 Windows 窗体控件](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)。  
  
 在创作用于数据绑定方案的控件时，应实现以下数据绑定特性之一：  
  
|数据绑定属性用法|  
|-----------------------------------|  
|在简单控件上实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>（如 <xref:System.Windows.Forms.TextBox>），此类控件用于显示数据的单个列（或属性）。 （本演练页面描述了此过程）。|  
|在控件上实现 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>（如 <xref:System.Windows.Forms.DataGridView>），此类控件用于显示数据列表（或表）。 有关详细信息，请参阅[创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|  
|在控件上实现 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>（如 <xref:System.Windows.Forms.ComboBox>），此类控件用于显示数据列表（或表），也需要显示数据的单个列或属性。 有关详细信息，请参阅[创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|  
  
 本演练创建了一个简单控件，用于显示表中单个列的数据。 此示例使用 Northwind 示例数据库的 `Phone` 表中的 `Customers` 列。 简单的用户控件将通过使用标准的电话号码格式，显示客户的电话号码<xref:System.Windows.Forms.MaskedTextBox>和设置的电话号码的掩码。  
  
 在本演练中，你将学会如何执行以下任务：  
  
-   创建一个新**Windows 窗体应用程序**。  
  
-   添加新**用户控件**到你的项目。  
  
-   以可视方式设计用户控件。  
  
-   实现 `DefaultBindingProperty` 特性。  
  
-   创建具有的数据集**数据源配置**向导。  
  
-   设置**Phone**中的列**数据源**窗口，以使用新的控件。  
  
-   创建一个用于在新控件中显示数据的窗体。  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**数据存储和处理**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
## <a name="create-a-windows-forms-application"></a>创建 Windows 窗体应用程序  
 第一步是创建**Windows 窗体应用程序**。  
  
#### <a name="to-create-the-new-windows-project"></a>创建新的 Windows 项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**SimpleControlWalkthrough**，然后选择**确定**。 
  
     **SimpleControlWalkthrough**项目时创建，并添加到**解决方案资源管理器**。  
  
## <a name="add-a-user-control-to-the-project"></a>向项目添加用户控件  
 本演练将创建一个简单的数据绑定控件从**用户控件**，因此添加**用户控件**项以**SimpleControlWalkthrough**项目。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>将用户控件添加到项目中  
  
1.  从**项目**菜单上，选择**添加用户控件**。  
  
2.  类型`PhoneNumberBox`名称区域中，然后单击**添加**。  
  
     **PhoneNumberBox**控件添加到**解决方案资源管理器**，并在设计器中打开。  
  
## <a name="design-the-phonenumberbox-control"></a>设计 PhoneNumberBox 控件  
 本演练对现有 <xref:System.Windows.Forms.MaskedTextBox> 进行了扩展，以创建 `PhoneNumberBox` 控件。  
  
#### <a name="to-design-the-phonenumberbox-control"></a>设计 PhoneNumberBox 控件  
  
1.  拖动<xref:System.Windows.Forms.MaskedTextBox>从**工具箱**到该用户控件的设计图面上。  
  
2.  选择智能标记上<xref:System.Windows.Forms.MaskedTextBox>你刚刚拖放，并选择**设置掩码**。  
  
3.  选择**电话号码**中**输入掩码**对话框中，单击**确定**以设置掩码。  
  
## <a name="add-the-required-data-binding-attribute"></a>添加所需的数据绑定特性  
 对于支持数据绑定的简单控件，应实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>。  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>实现 DefaultBindingProperty 特性  
  
1.  将 `PhoneNumberBox` 控件切换到代码视图。 (在**视图**菜单上，选择**代码**。)  
  
2.  将 `PhoneNumberBox` 中的代码替换为以下内容：  
  
     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  从 **“生成”** 菜单中选择 **“生成解决方案”**。  
  
## <a name="create-a-data-source-from-your-database"></a>从您的数据库创建数据源  
 此步骤使用**数据源配置**向导创建数据源基于`Customers`Northwind 示例数据库中的表。 你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。 设置 Northwind 示例数据库的信息，请参阅[如何： 安装示例数据库](../data-tools/installing-database-systems-tools-and-samples.md)。  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  在 **“数据”** 菜单上，单击 **“显示数据源”**。  
  
2.  在**数据源**窗口中，选择**添加新数据源**启动**数据源配置**向导。  
  
3.  上**选择数据源类型**页上，选择**数据库**，然后单击**下一步**。  
  
4.  上**选择你的数据连接**页上，执行下列操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
    -   选择**新连接**以启动**添加/修改连接**对话框。  
  
5.  如果你的数据库需要密码，请选择该选项以包括敏感数据，然后单击**下一步**。  
  
6.  上**将连接字符串保存到应用程序配置文件**页上，单击**下一步**。  
  
7.  上**选择数据库对象**页上，展开**表**节点。  
  
8.  选择`Customers`表，并依次**完成**。  
  
     **NorthwindDataSet**添加到你的项目，与`Customers`表将出现在**数据源**窗口。  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>将 phone 列使用 phonenumberbox 控件设置  
 在**数据源**窗口中，你可以设置然后再将项拖动到窗体中创建的控件。  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>将“电话”列设置为绑定到“PhoneNumberBox”控件  
  
1.  打开**Form1**设计器中。  
  
2.  展开**客户**中的节点**数据源**窗口。  
  
3.  单击下拉箭头**客户**节点，然后选择**详细信息**从控件列表。  
  
4.  单击下拉箭头**Phone**列中，选择**自定义**。  
  
5.  选择**PhoneNumberBox**从列表中**关联的控件**中**数据 UI 自定义选项**对话框。  
  
6.  单击下拉箭头**Phone**列中，选择**PhoneNumberBox**。  
  
## <a name="add-controls-to-the-form"></a>将控件添加到窗体  
 你可以通过将某些项从创建数据绑定控件**数据源**拖到窗体的窗口。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>在窗体上创建数据绑定控件  
  
-   将主**客户**节点从**数据源**窗口拖到窗体，并确认`PhoneNumberBox`控件用于显示中的数据`Phone`列。  
  
     带有描述性标签的数据绑定控件将显示在窗体上，同时还显示一个工具条 (<xref:System.Windows.Forms.BindingNavigator>)，用于在记录间进行导航。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)，CustomersTableAdapter， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。  
  
## <a name="run-the-application"></a>运行此应用程序  
  
#### <a name="to-run-the-application"></a>要运行应用程序  
  
-   按 F5 运行该应用程序。  
  
## <a name="next-steps"></a>后续步骤  
 根据应用程序的需求，在创建了支持数据绑定的控件后，可能还需要执行一些步骤。 接下来的一些常见步骤包括：  
  
-   将你的自定义控件置于控件库中，以便在其他应用程序中重用它们。  
  
-   创建支持更复杂的数据绑定方案的控件。 有关详细信息，请参阅[创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)和[创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
