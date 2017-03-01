---
title: "创建 Windows 窗体工具箱控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 770963e06655c0d4da2946fa7981fd1e4496b7f0
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-toolbox-control"></a>创建 Windows 窗体工具箱控件
Visual Studio 扩展性工具 (VS SDK) 中包含的 Windows 窗体工具箱控件项模板允许您创建的控件，将自动添加到**工具箱**安装扩展的安装。 本主题演示如何使用模板来创建一个简单的计数器控件，可以将它们分发给其他用户。  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>创建 Windows 窗体工具箱控件  
 Windows 窗体工具箱控件模板创建的未定义的用户控件，并提供了将控件添加到所需的功能的所有**工具箱**。  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>使用 Windows 窗体工具箱控件创建扩展  
  
1.  创建一个名为的 VSIX 项目`MyWinFormsControl`。 您可以找到中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  在打开该项目，添加**Windows 窗体工具箱控件**项模板名为`Counter`。 在**解决方案资源管理器**，用鼠标右键单击项目节点并选择**添加 / 新项**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**，然后选择**工具箱的 Windows 窗体控件**  
  
3.  这会将添加一个用户控件， `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>放置在控件**工具箱**，和一个**Microsoft.VisualStudio.ToolboxControl**资产部署的 VSIX 清单中的条目。</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>  
  
### <a name="building-a-user-interface-for-the-control"></a>构建控件的用户界面  
 `Counter`控件需要两个子控件︰<xref:System.Windows.Forms.Label>若要显示的当前计数和<xref:System.Windows.Forms.Button>的计数重置为 0。</xref:System.Windows.Forms.Button> </xref:System.Windows.Forms.Label> 需要其他任何子控件不，因为调用方将以编程方式递增计数器。  
  
##### <a name="to-build-the-user-interface"></a>构建用户界面  
  
1.  在**解决方案资源管理器**，双击 Counter.cs 在设计器中打开它。  
  
2.  删除"单击此处 ！" **按钮**的是默认情况下添加时，包含 Windows 窗体工具箱控件项模板。  
  
3.  从**工具箱**，拖动`Label`控件，然后`Button`它下面到设计图面上的控件。  
  
4.  调整为 150 总体的用户控件的大小、 50 像素，并且调整大小按钮控制为 50，20 个像素。  
  
5.  在**属性**窗口中，设置以下值在设计图面上的控件。  
  
    |控件|属性|值|  
    |-------------|--------------|-----------|  
    |`Label1`|**文本**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**文本**|重置|  
  
### <a name="coding-the-user-control"></a>编码用户控件  
 `Counter` 控件将公开一个用于递增计数器的方法、一个计数器每次递增时均会引发的事件、一个 `Reset` 按钮，以及&3; 个存储当前计数、显示文本及是显示还是隐藏 `Reset` 按钮的属性。 `ProvideToolboxControl`属性确定在何处**工具箱**`Counter`控件将出现。  
  
##### <a name="to-code-the-user-control"></a>编写用户控件的代码  
  
1.  双击要在代码窗口中打开其 load 事件处理程序的窗体。  
  
2.  事件处理程序方法中，上面控件类中创建一个整数来存储该计数器值和一个字符串，用于存储显示文本，如下面的示例中所示。  
  
    ```c#  
    int currentValue;  
    string displayText;  
    ```  
  
3.  创建以下公共属性声明。  
  
    ```c#  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     调用方可以访问这些属性来获取和设置的显示文本的计数器来显示或隐藏`Reset`按钮。 调用方可以获取的当前值的只读的`Value`属性，但它们不能直接设置的值。  
  
4.  将以下代码放入`Load`控件的事件。  
  
    ```c#  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     设置**标签**中文<xref:System.Windows.Forms.UserControl.Load>事件使要加载之前应用它们的值的目标属性。</xref:System.Windows.Forms.UserControl.Load> 设置**标签**构造函数中的文本将产生一个空**标签**。  
  
5.  创建要递增计数器的下列公共方法。  
  
    ```c#  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  添加一个声明`Incremented`到控件类的事件。  
  
    ```c#  
    public event EventHandler Incremented;  
    ```  
  
     调用方可以添加到此事件，以对此计数器的值变化作出响应的处理程序。  
  
7.  返回设计视图，然后双击`Reset`按钮以生成`btnReset_Click`事件处理程序，然后在下面的示例中所示填充。  
  
    ```c#  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  类定义上方紧挨在`ProvideToolboxControl`特性声明，将从第一个参数的值更改`"MyWinFormsControl.Counter"`到`"General"`。 这会设置将在“工具箱” 中托管控件的项组名称。  
  
     以下示例演示了 `ProvideToolboxControl` 特性和调整后的类定义。  
  
    ```c#  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>测试控件  
 若要测试**工具箱**控制、 首次在开发环境中对它进行测试和已编译的应用程序中对其进行测试。  
  
##### <a name="to-test-the-control"></a>测试控件  
  
1.  按 F5。  
  
     这将生成项目并打开已安装该控件的 Visual Studio 的第二个实验实例。  
  
2.  在 Visual Studio 的实验实例中，创建**Windows 窗体应用程序**项目。  
  
3.  在**解决方案资源管理器**，双击 Form1.cs 如果尚未打开在设计器中打开。  
  
4.  在**工具箱**、`Counter`控件应显示在**常规**部分。  
  
5.  拖动`Counter`控制转移到您的窗体，然后选择它。 `Value`， `Message`，和`ShowReset`属性将显示在**属性**窗口中，以及从<xref:System.Windows.Forms.UserControl>。</xref:System.Windows.Forms.UserControl>继承的属性  
  
6.  将 `Message` 属性设置为 `Count:`。  
  
7.  拖动<xref:System.Windows.Forms.Button>控制转移到该窗体，并将该按钮的名称和文本属性`Test`。</xref:System.Windows.Forms.Button>  
  
8.  双击按钮以在代码视图中打开 Form1.cs，并创建一个 click 处理程序。  
  
9. 在单击处理程序中，调用`counter1.Increment()`。  
  
10. 在构造函数，在调用后`InitializeComponent`，类型`counter1``.``Incremented +=`然后按 tab 键两次。  
  
     Visual Studio 将生成窗体级别处理程序`counter1.Incremented`事件。  
  
11. 突出显示`Throw`事件处理程序类型中的语句`mbox`，然后按 tab 键两次，以与 mbox 代码段中生成一个消息框。  
  
12. 在下一行中，将以下代码添加`if` / `else`块来设置可见性`Reset`按钮。  
  
    ```c#  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. 按 F5。  
  
     打开窗体。 `Counter`控件将显示以下文本。  
  
     **计数︰ 0**  
  
14. 单击“测试” 。  
  
     计数器递增和 Visual Studio 显示一个消息框。  
  
15. 关闭消息框。  
  
     **重置**按钮就会消失。  
  
16. 单击**测试**直到该计数器达到**5**关闭消息框每次。  
  
     **重置**按钮再次出现。  
  
17. 单击“重置” 。  
  
     该计数器将重置为**0**。  
  
## <a name="next-steps"></a>后续步骤  
 生成“工具箱”  控件时，Visual Studio 将在项目的 \bin\debug\ 文件夹中创建一个名为 *项目名称*.vsix 的文件。 你可以通过将 .vsix 文件上载到网络或网站来部署此控件。 当用户打开.vsix 文件时，该控件被安装，并添加到 Visual Studio**工具箱**在用户计算机上。 或者，可以将上载到的.vsix 文件[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)Web 站点，以便用户能够找到它通过在浏览**工具 / 扩展和更新**对话框。  
  
## <a name="see-also"></a>另请参阅  
 [扩展工具箱](../misc/extending-the-toolbox.md)   
 [创建 WPF 工具箱控件](../extensibility/creating-a-wpf-toolbox-control.md)   
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Windows 窗体控件开发基础知识](http://msdn.microsoft.com/Library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)
