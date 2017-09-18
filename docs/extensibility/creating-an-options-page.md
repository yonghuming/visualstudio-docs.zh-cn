---
title: "创建选项页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“工具选项”页 [Visual Studio SDK]，创建"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 62
---
# 创建选项页
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练中创建一个使用属性网格可以查看和设置属性的简单工具 \/ 选项页。  
  
 要保存到这些属性，并将其还原从设置文件，请执行下列步骤，然后参阅 [创建设置类别](../extensibility/creating-a-settings-category.md)。  
  
 MPF 提供两个类可帮助您创建工具选项页 <xref:Microsoft.VisualStudio.Shell.Package> 类和 <xref:Microsoft.VisualStudio.Shell.DialogPage> 类。 您创建的 VSPackage，若要通过子类化包类为这些页面提供一个容器。 通过从 DialogPage 类派生来创建每个工具选项页。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建工具选项网格页  
 在本部分中，您将创建一个简单的工具选项属性网格。 使用此网格可显示和更改属性的值。  
  
#### 若要创建 VSIX 项目并添加 VSPackage  
  
1.  每个 Visual Studio 的扩展从一个 VSIX 部署项目，它将包含的扩展资产开始。 创建 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 项目名为 `MyToolsOptionsExtension`。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\# \/ 可扩展性**。  
  
2.  通过添加一个名为 Visual Studio Package 项目模板来添加 VSPackage `MyToolsOptionsPackage`。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项对话框**, ，请转到 **Visual C\# 项 \/ 扩展性** ，然后选择 **Visual Studio Package**。 在 **名称** 在对话框底部字段中，文件将名称更改为 `MyToolsOptionsPackage.cs`。 有关如何创建 VSPackage 的详细信息，请参阅 [使用 VSPackage 创建扩展](../extensibility/creating-an-extension-with-a-vspackage.md)。  
  
#### 若要创建的工具选项属性网格  
  
1.  在代码编辑器中打开 MyToolsOptionsPackage 文件。  
  
2.  添加以下 using 语句。  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  声明一个 OptionPageGrid 类和派生它从 <xref:Microsoft.VisualStudio.Shell.DialogPage>。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  应用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 到 VSPackage 类，以分配给类的选项类别和 OptionPageGrid 选项页名称。 结果应如下所示︰  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  添加 `OptionInteger` 属性设置为 `OptionPageGrid` 类。  
  
    -   应用 <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> 要赋给属性的属性网格类别。  
  
    -   应用 <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> 分配给属性的名称。  
  
    -   应用 <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> 要赋给属性说明。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  默认实现 <xref:Microsoft.VisualStudio.Shell.DialogPage> 支持的属性，具有相应的转换器或作为结构或可以扩展为具有相应的转换器的属性的数组。 有关转换器的列表，请参阅 <xref:System.ComponentModel> 命名空间。  
  
6.  生成项目并启动调试。  
  
7.  Visual Studio 的实验实例中在 **工具** 菜单上，单击 **选项**。  
  
     在左窗格中您应该看到 **My Category**。 （选项类别是按字母顺序列出，以便它才会显示有关中途列表中向下。） 打开 **My Category** ，然后单击 **我的网格页**。选项网格将显示在右窗格中。 属性类别是 **我选项**, ，并且属性名称为 **我整数选项**。 属性说明 **我整数选项**, ，将显示在窗格的底部。 值从 256 其初始值更改为其他内容。 单击 **确定**, ，然后再重新打开 **我的网格页**。 您可以看到新值仍然存在。  
  
     选项页它也可通过 Visual Studio 快速启动。 在 IDE 右上角中的快速启动窗口中，键入 **My Category** ，您将看到 **My Category –\> 我的网格页** 的下拉列表中列出。  
  
## 创建工具选项自定义页  
 在此部分中，可以使用自定义用户界面创建工具选项页。 使用此页可显示和更改属性的值。  
  
1.  在代码编辑器中打开 MyToolsOptionsPackage 文件。  
  
2.  添加以下 using 语句。  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  添加 `OptionPageCustom` 类，再 `OptionPageGrid` 类。 派生新类从 `DialogPage`。  
  
    ```c#  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  将 GUID 属性添加。 添加 OptionString 属性︰  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  应用第二个 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 到 VSPackage 类。 此属性分配类的选项类别和选项页名称。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  添加一个新 **用户控件** 名 MyUserControl 为到该项目。  
  
7.  添加 **TextBox** 向该用户控件的控件。  
  
     在 **属性** 窗口中的，在工具栏上，单击 **事件** 按钮，然后再双击 **保留** 事件。 MyUserControl.cs 代码中出现新的事件处理程序。  
  
8.  添加一个公共 `OptionsPage` 字段中， `Initialize` 方法在控件类中与事件处理程序，以设置选项值的文本框中内容的更新︰  
  
    ```c#  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     `optionsPage` 字段保存到父级的引用 `OptionPageCustom` 实例。`Initialize` 方法将显示 `OptionString` 中 **TextBox**。 事件处理程序写入的当前值 **TextBox** 到 `OptionString` 当焦点叶 **TextBox**。  
  
9. 在包的代码文件中，添加覆盖 `OptionPageCustom.Window` 属性设置为要创建、 初始化和返回的一个实例的 OptionPageCustom 类 `MyUserControl`。 该类现在应如下所示︰  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. 生成并运行该项目。  
  
11. 在实验实例中，单击 **工具 \/ 选项**。  
  
12. 查找 **我类别** 然后 **我的自定义页面**。  
  
13. 值更改 **OptionString**。 单击 **确定**, ，然后再重新打开 **我的自定义网页**。 您可以看到新值已持久化。  
  
## 访问选项  
 在本部分中，从 VSPackage 承载相关联的工具选项页获取选项的值。 可以使用相同的方法来获取任何公共属性的值。  
  
1.  在包的代码文件中，添加一个名为的公共属性 **OptionInteger** 到 **MyToolsOptionsPackage** 类。  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     此代码将调用 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 创建或检索 `OptionPageGrid` 实例。`OptionPageGrid` 调用 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> 加载其选项，它们是公共属性。  
  
2.  现在，添加一个名为的自定义命令项模板 **MyToolsOptionsCommand** 显示的值。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **自定义命令**。 在 **名称** 在窗口的底部字段中，命令文件名称更改为 **MyToolsOptionsCommand.cs**。  
  
3.  在 MyToolsOptionsCommand 文件中，替换该命令的正文 `ShowMessageBox` 替换为以下方法︰  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  生成项目并启动调试。  
  
5.  在实验实例中，在 **工具** 菜单上，单击 **调用 MyToolsOptionsCommand**。  
  
     一个消息框显示的当前值 `OptionInteger`。  
  
## 请参阅  
 [选项和选项页](../extensibility/internals/options-and-options-pages.md)