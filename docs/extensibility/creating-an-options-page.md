---
title: "创建选项页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 10b40fccecfff4d4578b1a1bfe228d037e7516ac
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-options-page"></a>创建选项页
本演练创建一个简单工具/选项页面属性网格用于检查和设置属性。  
  
 若要保存到这些属性，并从设置文件中还原，请执行下列步骤，然后查看[创建设置类别](../extensibility/creating-a-settings-category.md)。  
  
 MPF 提供了两个类来帮助你创建工具选项页<xref:Microsoft.VisualStudio.Shell.Package>类和<xref:Microsoft.VisualStudio.Shell.DialogPage>类。 你创建 VSPackage 来通过子类化包类为这些页面提供一个容器。 通过从 DialogPage 类派生创建每个工具选项页。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-tools-options-grid-page"></a>创建工具选项网格页  
 在本部分中，你将创建一个简单的工具选项属性网格。 使用此网格可以显示和更改属性的值。  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>若要创建 VSIX 项目并添加 VSPackage  
  
1.  每个 Visual Studio 扩展开头 VSIX 部署项目将包含扩展资产。 创建[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名为 VSIX 项目`MyToolsOptionsExtension`。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  通过添加一个名为的 Visual Studio 包项目模板添加 VSPackage `MyToolsOptionsPackage`。 在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 在**添加新项对话框**，请转到**Visual C# 项 / 扩展性**和选择**Visual Studio 包**。 在**名称**在对话框底部字段中，文件名称更改为`MyToolsOptionsPackage.cs`。 有关如何创建 VSPackage 的详细信息，请参阅[使用 VSPackage 创建扩展](../extensibility/creating-an-extension-with-a-vspackage.md)。  
  
#### <a name="to-create-the-tools-options-property-grid"></a>若要创建工具选项属性网格  
  
1.  在代码编辑器中打开 MyToolsOptionsPackage 文件。  
  
2.  添加以下 using 语句。  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  声明 OptionPageGrid 类和派生从<xref:Microsoft.VisualStudio.Shell.DialogPage>。  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  应用<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>到 VSPackage 类，以分配给类的选项类别和 OptionPageGrid 选项页名称。 结果应如下所示：  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  添加`OptionInteger`属性`OptionPageGrid`类。  
  
    -   应用<xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>要赋给属性的属性网格类别。  
  
    -   应用<xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>将名称分配给属性。  
  
    -   应用<xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>要赋给属性说明。  
  
    ```csharp  
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
    >  默认实现<xref:Microsoft.VisualStudio.Shell.DialogPage>支持的属性具有相应的转换器或者为结构或可以将扩展到具有相应的转换器的属性的数组。 有关转换器的列表，请参阅<xref:System.ComponentModel>命名空间。  
  
6.  生成项目并启动调试。  
  
7.  在实验实例中的 Visual Studio 中，在**工具**菜单上，单击**选项**。  
  
     在左窗格中你应该看到**我类别**。 （选项类别是按字母顺序列出，因此它才会显示有关便中途下列表。）打开**我类别**，然后单击**我网格页**。选项网格将显示在右窗格中。 属性类别**我选项**，并且属性名称为**我整数选项**。 属性说明中，**我整数选项**，窗格的底部将显示。 更改从 256 其初始值为其他值。 单击**确定**，然后重新打开**我网格页**。 你可以看到新的值仍然存在。  
  
     选项页也会提供通过 Visual Studio 的快速启动。 在 IDE 右上角中的快速启动窗口中，键入**我类别**，你将看到**我类别-> 我的网格网页**下拉列表中列出。  
  
## <a name="creating-a-tools-options-custom-page"></a>创建工具选项自定义页  
 在此部分中，可以使用自定义 UI 创建工具选项页。 使用此页可显示和更改属性的值。  
  
1.  在代码编辑器中打开 MyToolsOptionsPackage 文件。  
  
2.  添加以下 using 语句。  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  添加`OptionPageCustom`类，之前`OptionPageGrid`类。 派生新类从`DialogPage`。  
  
    ```csharp  
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
  
4.  添加 GUID 特性。 添加 OptionString 属性：  
  
    ```csharp  
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
  
5.  应用第二个<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>到 VSPackage 类。 此属性将分配类的选项类别和选项页名称。  
  
    ```csharp  
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
  
6.  添加新**用户控件**名 MyUserControl 为到项目。  
  
7.  添加**文本框中**到用户控件的控件。  
  
     在**属性**窗口中的，在工具栏上，单击**事件**按钮，，然后双击**保留**事件。 MyUserControl.cs 代码中出现新的事件处理程序。  
  
8.  添加公共`OptionsPage`字段，`Initialize`控件类和事件处理程序来设置选项值到文本框中的内容的更新的方法：  
  
    ```csharp  
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
  
     `optionsPage`字段包含对父级的引用`OptionPageCustom`实例。 `Initialize`方法显示`OptionString`中**文本框中**。 事件处理程序的当前值写入**文本框中**到`OptionString`当焦点叶**文本框中**。  
  
9. 在包代码文件中，添加的替代`OptionPageCustom.Window`到 OptionPageCustom 类，以创建、 初始化和返回的实例的属性`MyUserControl`。 类现在应如下所示：  
  
    ```csharp  
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
  
11. 在实验实例中，单击**工具 / 选项**。  
  
12. 查找**我类别**然后**我的自定义页**。  
  
13. 更改的值**OptionString**。 单击**确定**，然后重新打开**我的自定义网页**。 你可以看到新值已持久化。  
  
## <a name="accessing-options"></a>访问选项  
 本部分中的承载相关的工具选项页的 VSPackage 你获取某个选项的值。 可以使用相同的技术来获取任何公共属性的值。  
  
1.  在包代码文件中，添加一个名为的公共属性**OptionInteger**到**MyToolsOptionsPackage**类。  
  
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
  
     此代码调用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>创建或检索`OptionPageGrid`实例。 `OptionPageGrid`调用<xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>加载其选项，它们为公共属性。  
  
2.  现在，添加名为的自定义命令项模板**MyToolsOptionsCommand**显示的值。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**自定义命令**。 在**名称**在窗口底部字段中，命令文件名称更改为**MyToolsOptionsCommand.cs**。  
  
3.  在 MyToolsOptionsCommand 文件中，该命令的主体替换`ShowMessageBox`方法替换为以下：  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  生成项目并启动调试。  
  
5.  在实验实例中，在**工具**菜单上，单击**调用 MyToolsOptionsCommand**。  
  
     一个消息框显示的当前值`OptionInteger`。  
  
## <a name="see-also"></a>另请参阅  
 [选项和选项页](../extensibility/internals/options-and-options-pages.md)
