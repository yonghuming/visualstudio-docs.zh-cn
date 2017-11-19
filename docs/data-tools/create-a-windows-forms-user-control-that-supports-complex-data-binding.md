---
title: "创建与数据绑定的 Windows 窗体用户控件 |Microsoft 文档"
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 8b23bfe7c30988a80904377e583a5a5f6d4cd2ff
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>创建支持复杂数据绑定的 Windows 窗体用户控件
当在 Windows 应用程序中的窗体上显示数据，你可以选择从现有控件**工具箱**，或如果你的应用程序需要在标准控件中不可用的功能，还可以创作自定义控件。 本演练显示了如何创建实现 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控件。 实现 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 的控件包含可以绑定到数据的 `DataSource` 和 `DataMember` 属性。 此类控件是类似于<xref:System.Windows.Forms.DataGridView>或<xref:System.Windows.Forms.ListBox>  
  
 有关控件创作的详细信息，请参阅[在设计时开发 Windows 窗体控件](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)。  
  
 创作用于数据绑定方案的控件时需要实现以下数据绑定特性之一：  
  
|数据绑定属性用法|  
|-----------------------------------|  
|在简单控件上实现 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>（如 <xref:System.Windows.Forms.TextBox>），此类控件用于显示数据的单个列（或属性）。 有关详细信息，请参阅[创建支持简单数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。|  
|在控件上实现 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>（如 <xref:System.Windows.Forms.DataGridView>），此类控件用于显示数据列表（或表）。 （本演练页面描述了此过程）。|  
|在控件上实现 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>（如 <xref:System.Windows.Forms.ComboBox>），此类控件用于显示数据列表（或表），也需要显示数据的单个列或属性。 有关详细信息，请参阅[创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|  
  
 本演练创建显示表中多行数据的复杂控件。 本示例使用源自 Northwind 示例数据库的 `Customers` 表。 复杂用户控件将会在自定义控件中的 <xref:System.Windows.Forms.DataGridView> 中显示 Customers 表。  
  
 在本演练中，你将学会如何执行以下任务：  
  
-   创建一个新**Windows 窗体应用程序**。  
  
-   添加新**用户控件**到你的项目。  
  
-   以可视方式设计用户控件。  
  
-   实现 `ComplexBindingProperty` 特性。  
  
-   创建具有的数据集[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)。  
  
-   设置**客户**表中[数据源窗口](add-new-data-sources.md)以使用新的复杂控件。  
  
-   通过将其从添加新控件**数据源窗口**到**Form1**。  
  
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

4. 将项目**命名为 ComplexControlWalkthrough**，然后选择**确定**。 
  
     **命名为 ComplexControlWalkthrough**项目时创建，并添加到**解决方案资源管理器**。  
  
## <a name="add-a-user-control-to-the-project"></a>向项目添加用户控件  
 由于此演练创建复杂数据绑定控件从**用户控件**，必须添加**用户控件**到项目的项。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>将用户控件添加到项目中  
  
1.  从**项目**菜单上，选择**添加用户控件**。  
  
2.  类型**ComplexDataGridView**中**名称**区域中，，然后单击**添加**。  
  
     **ComplexDataGridView**控件添加到**解决方案资源管理器**，并在设计器中打开。  
  
## <a name="design-the-complexdatagridview-control"></a>设计 ComplexDataGridView 控件  
 此步骤将 <xref:System.Windows.Forms.DataGridView> 添加到该用户控件。  
  
#### <a name="to-design-the-complexdatagridview-control"></a>设计 ComplexDataGridView 控件  
  
-   拖动<xref:System.Windows.Forms.DataGridView>从**工具箱**到该用户控件的设计图面上。  
  
## <a name="add-the-required-data-binding-attribute"></a>添加所需的数据绑定特性  
 对于支持数据绑定的复杂控件，你可以实现 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>。  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>实现 ComplexBindingProperties 特性  
  
1.  交换机**ComplexDataGridView**控件添加到代码视图。 (在**视图**菜单上，选择**代码**。)  
  
2.  将 `ComplexDataGridView` 中的代码替换为以下内容：  
  
     [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  从 **“生成”** 菜单中选择 **“生成解决方案”**。  
  
## <a name="creating-a-data-source-from-your-database"></a>从您的数据库创建数据源  
此步骤使用**数据源配置**向导创建数据源基于`Customers`Northwind 示例数据库中的表。  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  在 **“数据”** 菜单上，单击 **“显示数据源”**。  
  
2.  在**数据源**窗口中，选择**添加新数据源**启动**数据源配置**向导。  
  
3.  在 **“选择数据源类型”** 页上选择 **“数据库”** ，然后单击 **“下一步”**。  
  
4.  上**选择你的数据连接**页上，执行下列操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
    -   选择**新连接**以启动**添加/修改连接**对话框。  
  
5.  如果你的数据库需要密码，请选择该选项以包括敏感数据，然后单击**下一步**。  
  
6.  上**将连接字符串保存到应用程序配置文件**页上，单击**下一步**。  
  
7.  上**选择数据库对象**页上，展开**表**节点。  
  
8.  选择`Customers`表，并依次**完成**。  
  
     **NorthwindDataSet**添加到你的项目，与`Customers`表将出现在**数据源**窗口。  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>设置 Customers 表以使用 ComplexDataGridView 控件  
 在**数据源**窗口中，你可以设置然后再将项拖动到窗体中创建的控件。  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>设置 Customers 表以绑定到 ComplexDataGridView 控件  
  
1.  打开**Form1**设计器中。  
  
2.  展开**客户**中的节点**数据源**窗口。  
  
3.  单击下拉箭头**客户**节点，然后选择**自定义**。  
  
4.  选择**ComplexDataGridView**从列表中**关联的控件**中**数据 UI 自定义选项**对话框。  
  
5.  单击下拉箭头`Customers`表，，然后选择**ComplexDataGridView**从控件列表。  
  
## <a name="add-controls-to-the-form"></a>将控件添加到窗体  
 你可以通过将某些项从创建数据绑定控件**数据源**拖动到窗体的窗口。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>在窗体上创建数据绑定控件  
  
-   将主**客户**节点从**数据源**拖到窗体的窗口。验证**ComplexDataGridView**控件用于显示表的数据。  
  
## <a name="running-the-application"></a>运行应用程序  
  
#### <a name="to-run-the-application"></a>要运行应用程序  
  
-   按 F5 运行该应用程序。  
  
## <a name="next-steps"></a>后续步骤  
 根据应用程序的需求，在创建了支持数据绑定的控件后，还可能需要执行一些步骤。 接下来的一些常见步骤包括：  
  
-   将你的自定义控件置于控件库中，以便在其他应用程序中重用它们。  
  
-   创建支持查找方案的控件。 有关详细信息，请参阅[创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [设置从数据源窗口拖动时创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows 窗体控件](/dotnet/framework/winforms/controls/index)
