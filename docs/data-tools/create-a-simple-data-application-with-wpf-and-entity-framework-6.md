---
title: "使用 WPF 和 Entity Framework 6 中创建一个简单的数据应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 24d6401cae58b0bede44519900f6d72bd77ab2a9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>使用 WPF 和 Entity Framework 6 中创建一个简单的数据应用程序
本演练演示如何使用 SQL Server LocalDB、 Northwind 数据库，Entity Framework 6 和 Windows Presentation Foundation 的 Visual Studio 中创建基本"forms over data"应用程序。 它演示如何执行与主-详细信息视图中，基本数据绑定，它还提供自定义"绑定导航器"的"移动上的下一步"按钮，使用"移动上一个""将移动到开头，""移至最后，""更新"和"删除"。  
  
 本文重点介绍在 Visual Studio 中，使用数据工具并不会尝试解释中任何深度的基础技术。 它假定您有基本熟悉 XAML、 实体框架和 SQL。 此示例也并不演示模型-视图-视图模型 (MVVM) 体系结构，它是用于 WPF 应用程序的标准。 但是，你可以将此代码复制到自己 MVVM 的应用程序很少需进行任何修改。  
  
## <a name="install-and-connect-to-northwind"></a>安装并连接到 Northwind  
此示例使用 SQL Server Express LocalDB 和 Northwind 示例数据库。 它应运行与其他 SQL 数据库产品同样，如果该产品的 ADO.NET 数据提供程序支持实体框架。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**.NET 桌面开发**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
3.  [添加新连接](../data-tools/add-new-connections.md)罗斯文。  
  
## <a name="configure-the-project"></a>配置项目  
  
1.  在 Visual Studio 中，选择**文件**，**新建**，**项目...** ，然后创建一个新 C# WPF 应用程序。  
  
2.  接下来我们将为 Entity Framework 6 添加 NuGet 包。 在解决方案资源管理器，选择项目节点。 在主菜单中，选择**项目**，**管理 NuGet 包...**  
  
     ![管理 NuGet 包菜单项](../data-tools/media/raddata_vs2015_manage_nuget_packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  在 NuGet 包管理器中，单击**浏览**链接。 实体框架可能是在列表中的顶层包。 单击**安装**右窗格中按照提示进行操作。 输出窗口将告诉您完成安装。  
  
     ![实体框架 NuGet 包](../data-tools/media/raddata_vs2015_nuget_ef.png "raddata_vs2015_Nuget_EF")  
  
4.  现在我们可以使用 Visual Studio 来创建基于 Northwind 数据库的模型。  
  
## <a name="create-the-model"></a>创建模型  
  
1.  右键单击解决方案资源管理器中的项目节点并选择**添加**，**新建项...**.在左窗格中，在 C# 节点下，选择**数据**和在中间窗格中选择**ADO.NET 实体数据模型**。  
  
     ![实体框架模型新项目项](../data-tools/media/raddata-ef-new-project-item.png "raddata EF 新项目项")  

  2.  调用模型`Northwind_model`，然后选择确定。 这将显示**实体数据模型向导**。 选择**EF 设计器从数据库**，然后单击**下一步**。  
  
     ![从数据库的 EF 模型](../data-tools/media/raddata-ef-model-from-database.png "raddata 从数据库的 EF 模型")  
  
3.  在下一个屏幕中，连接并单击选择 LocalDB Northwind**下一步**。  
  
4.  在向导的下一步页中，我们选择的表、 存储的过程和要包含在实体框架模型中其他数据库对象。 展开树视图中的 dbo 节点并选择客户、 订单和订单详细信息。 保留选中的默认值，然后单击**完成**。  
  
     ![选择数据库对象模型](../data-tools/media/raddata-choose-ef-objects.png "raddata 选择 EF 对象")  
  
5.  向导将生成表示实体框架模型的 C# 类。 这些是纯旧 C# 类和它们是我们将数据绑定到 WPF 用户界面。 .Edmx 文件描述关系和其他将类与数据库中的对象相关联的元数据。  .Tt 文件是生成的代码，将对模型进行操作并将更改保存到数据库的 T4 模板。 你可以看到所有这些文件在解决方案资源管理器 Northwind_model 节点下：  

       ![解决方案资源管理器 EF 模型文件](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata 解决方案资源管理器 EF 模型文件")  
  
     .Edmx 文件的设计器图面使您可以修改一些属性和关系在模型中。 我们不会在本演练中使用设计器。  
  
6.  .Tt 文件都通用，我们需要调整它们要使用 WPF 数据绑定，这需要 ObservableCollections 之一。  在解决方案资源管理器，展开 Northwind_model 节点，直到找到 Northwind_model.tt。 (请确保您是**不**中 *。上下文.tt 文件即正下方的.edmx 文件）。  
  
    -   替换的两个匹配项<xref:System.Collections.ICollection>与<xref:System.Collections.ObjectModel.ObservableCollection%601>。  
  
    -   替换第一个匹配项<xref:System.Collections.Generic.HashSet%601>与<xref:System.Collections.ObjectModel.ObservableCollection%601>围绕行 51。 不替换 HashSet 的第二个匹配项  
  
    -   替换的唯一匹配项<xref:System.Collections.Generic>（绕行 431） 与<xref:System.Collections.ObjectModel>。  
  
7.  按**Ctrl + Shift + B**以生成项目。 生成完成时，模型类会向数据源向导。  
  
现在我们已准备好挂钩到 XAML 页面此模型，以便我们可以查看、 导航和修改数据。  
  
## <a name="databind-the-model-to-the-xaml-page"></a>数据绑定到 XAML 页面模型  
 可以用来编写你自己的数据绑定代码，但可以更轻松地让 Visual Studio 为你完成此操作。  
  
1.  从主菜单中，选择**项目 > 添加新数据源**弹出**数据源配置向导**。 选择**对象**因为我们要绑定到的模型类不到数据库：  
  
     ![与对象源的数据源配置向导](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata 与对象源的数据源配置向导")  
  
2.  选择客户。  （的订单的源将自动生成中客户的订单导航属性。）  
  
     ![将实体类添加为数据源](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata 添加实体类作为数据源")  
  
3.  单击**完成**  
  
4.  导航到 MainWindow.xaml 在代码视图中。 我们将让此示例的目的非常简单的 XAML。 将主窗口的标题更改为更具说明性，并增加其高度和宽度到 600 x 800 现在。 你始终可以更改它更高版本。 现在到主网格中，一个行的导航按钮，一个用于客户的详细信息，一个用于显示其订单的网格中添加以下三个行定义：  

    ```xaml  
    <Grid.RowDefinitions>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="*"/>  
        </Grid.RowDefinitions>
    ```

5.  现在，以便你在设计器中查看它，打开 MainWindow.xaml。 这将导致数据源窗口显示为工具箱旁边的 Visual Studio 窗口距中的一个选项。 单击选项卡以打开窗口，或其他按**Shift + Alt + D**或选择**视图 &#124;其他 Windows &#124;数据源**。 我们将显示在其自己的单个文本框中的客户类中的每个属性。 第一次单击客户组合框中的箭头，然后选择**详细信息**。 然后，将节点拖到的中间部分的设计图面上，以便设计器知道你希望转中间行中。  如果你忘记放置位置，你可以手动更高版本在 XAML 中指定的行。 默认情况下这些控件都将置于垂直 grid 元素，但此时你可以按任何方式排列希望窗体上。  例如，可能会有用置于顶部，地址上面的名称文本框。 本文的示例应用程序对字段重新排序和重新为两列排列它们。  
  
     ![为单个控件的客户数据源绑定](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata 客户数据源绑定到单独的控件")  
  
     在代码视图中，你现在可以看到新`Grid`中元素的第 1 行 （中间行） 的父网格。 网格包含父`DataContext`属性指的是已添加到 CollectionViewSource`Windows.Resources`元素。 给定该数据上下文中，当第一个文本框中，例如，绑定进行"寻址"该名称映射到`Address`属性在当前`Customer`CollectionViewSource 中的对象。  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  

6.  当客户已在窗口的上半中可见时，想要查看在底部与其订单半双工。 我们将在单个网格视图控件中显示的订单。 对主-详细信息数据绑定按预期方式工作，这很重要，我们将绑定到客户类，不适用于单独的订单节点中的 Orders 属性。 请注意下图 ！ 将客户类的 Orders 属性拖到该窗体的下半部分，以便设计器将其放置在第 2 行：  
  
     ![为网格拖动订单类](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata 拖订单类为网格")  
  
7.  Visual Studio 生成了连接到模型中的事件的 UI 控件的所有绑定代码。 我们需要做，若要查看某些数据，是编写一些代码以填充模型。 第一个让我们导航到 MainWindow.xaml.cs，并将数据成员添加到的数据上下文 MainWindow 类。 为我们已生成，此对象的作用类似于下面的控件，可以跟踪更改，并在模型中的事件。 我们还将添加的构造函数初始化逻辑。 我们的类的顶部应如下所示：  
  
     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]  
     
     添加`using`指令 System.Data.Entity 若要将负载扩展方法引入作用域：  
  
     ```csharp
     using System.Data.Entity;  
     ```  

     现在向下滚动并查找 Window_Loaded 事件处理程序。 请注意为我们 Visual Studio 增加了 CollectionViewSource 对象。 这表示我们在创建模型时我们选择的 NorthwindEntities 对象。 让我们将代码添加到 Window_Loaded，以便整个方法现在如下所示：  

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]  

8.  按 F5 。 你应该看到已检索到 CollectionViewSource 的第一个客户的详细信息。 您还会看到他们在数据网格中的订单。 格式设置不太好，因此，让我们修复程序。 我们将创建一种方法，以查看其他记录并执行基本的 CRUD 操作。  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>调整页设计，并添加新的客户和订单的网格  
由 Visual Studio 生成的默认安排不适合我们的应用程序，因此我们将在 XAML 中手动进行一些更改。 我们还将需要一些"窗体"（它们都是实际网格），使用户能够添加新客户或订单。 我们需要一组单独的不是数据绑定到的文本框中，若要添加新的 customer 和 order `CollectionViewSource`。 我们将控制哪些用户将看到在任何给定时间处理程序方法中设置的可见属性的网格。 最后，我们将添加到订单网格，使用户能够删除单个订单中的每一行的删除按钮。  
  
首先，将这些样式添加到 MainWindow.xaml 中的 Windows.Resources 元素：  
  
```xaml  
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Left"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="23"/>  
</Style>  
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Right"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="26"/>  
    <Setter Property="Width" Value="120"/>  
</Style>  
```  
  
接下来，此标记替换整个外部网格：  
  
```xaml  
<Grid>  
     <Grid.RowDefinitions>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="*"/>  
     </Grid.RowDefinitions>   
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="New Order Form" FontWeight="Bold"/>  
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"  
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">  
         <DataGrid.Columns>  
             <DataGridTemplateColumn>  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>  
         </DataGrid.Columns>  
     </DataGrid>  
 </Grid>  
```  
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>添加按钮以导航、 添加、 更新和删除  
 在 Windows 窗体应用程序，可获取具有按钮的 BindingNavigator 对象在数据库中的行中导航和执行基本的 CRUD 操作。 WPF 不提供 BindingNavigator，但它也很简单创建一个。 我们将执行该操作使用按钮在水平 StackPanel，并且我们要将按钮使用绑定到方法后面的代码中的命令相关联。  
  
 有酣睡命令逻辑部分: （1） 命令、 （2） 绑定，（3) 按钮和 （4） 的命令处理程序的代码隐藏文件中。  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>在 XAML 中添加命令、 绑定和按钮  
  
1.  首先，让我们在 Windows.Resources 元素内我们 MainWindow.xaml 文件中添加命令：  
  
    ```xaml  
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>  
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>  
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>  
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>  
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>  
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>  
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>  
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>  
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>  
    ```  
  
2.  CommandBinding 将 RoutedUICommand 事件映射到背后的代码中的方法。 将此 CommandBindings 元素添加结束标记 Windows.Resources 之后：  
  
    ```xaml  
    <Window.CommandBindings>  
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>  
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>  
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>  
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>  
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>  
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>  
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>  
    </Window.CommandBindings>  
    ```  
  
3.  现在让我们添加具有导航 StackPanel、 添加、 删除和更新按钮。 首先，将此样式添加到 Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     其次，将此代码粘贴恰好在 XAML 页面顶部的外部的网格元素 RowDefinitions 后：  
  
    ```xaml  
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
    </StackPanel>  
    ```  
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>将命令处理程序添加到 MainWindow 类  
  
代码隐藏很短的添加和删除方法除外。 由 CollectionViewSource 的视图属性上调用方法执行导航。 DeleteOrderCommandHandler 演示如何对订单执行级联删除。 我们必须首先删除与之相关 Order_Details。 UpdateCommandHandler 将新客户或订单添加到集合，或者直接在文本框中的用户所做的更改更新现有的客户或订单。  
  
将这些处理程序方法添加到 MainWindow.xaml.cs 中的 MainWindow 类。 如果你 CollectionViewSource Customers 表具有不同的名称，然后你需要调整中每个这些方法的名称：  
  
[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]  
  
## <a name="run-the-application"></a>运行此应用程序
若要开始调试时，按**F5**。 你应看到客户和订单数据填充在网格中，并且导航按钮应该按预期方式工作。 单击"提交"以向模型添加新客户或订单后输入的数据。 单击"取消"退出而不保存数据的新客户或新订购窗体。 你可以向现有客户和订单直接在文本框中，进行编辑，并且这些更改自动写入到模型。  
  
## <a name="see-also"></a>请参阅
[适用于 NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)  
[实体框架文档](https://msdn.microsoft.com/en-us/data/ee712907.aspx)