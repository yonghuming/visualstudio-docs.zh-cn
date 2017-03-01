---
title: "创建自定义起始页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 2902ac3b5cd4fd038bdaf277a8390d5eb9e96b28
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-start-page"></a>创建自定义起始页
您可以按照本文档中的步骤来创建自定义的起始页。  
  
## <a name="creating-a-blank-start-page"></a>创建一个空白起始页  
 首先，请保留为空的起始页，通过创建具有 Visual Studio 将识别的标记结构的.xaml 文件。 然后，添加标记和代码隐藏页以产生外观和所需的功能。  
  
#### <a name="to-create-a-blank-start-page"></a>若要创建空的起始页  
  
1.  创建新的项目类型的**WPF 应用程序**(**Visual C# / Windows 桌面**。  
  
2.  添加对 `Microsoft.VisualStudio.Shell.14.0` 的引用。  
  
3.  在 XML 编辑器中打开 XAML 文件并将更改的顶级\<窗口&1;> 元素\<UserControl&1;> 不要删除任何命名空间声明的元素。  
  
4.  删除`x:Class`声明从顶级元素。 这使得 XAML 内容与 Visual Studio 工具窗口承载起始页兼容。  
  
5.  将以下命名空间声明添加到顶级\<UserControl&1;> 元素。  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     这些命名空间可用于访问 Visual Studio 命令、 控件和 UI 设置。 有关详细信息，请参阅[到起始页添加 Visual Studio 命令](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。  
  
     下面的示例演示在.xaml 文件中的标记为空的起始页。 任何自定义内容应进入内部<xref:System.Windows.Controls.Grid>元素。</xref:System.Windows.Controls.Grid>  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  将控件添加到空\<UserControl&1;> 元素以填充在你自定义起始页。 有关如何添加特定于 Visual Studio 的功能的信息，请参阅[到起始页添加 Visual Studio 命令](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。  
  
## <a name="testing-and-applying-the-custom-start-page"></a>测试并应用自定义起始页  
 未设置 Visual Studio 运行自定义起始页，直到您确认它不执行崩溃 Visual Studio 的主实例。 不过，测试实验实例中。  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>若要测试手动创建自定义起始页  
  
1.  将 XAML 文件中，和任何支持的文本文件或标记文件，为复制**%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ **文件夹。  
  
2.  如果你的起始页引用的任何控件或未安装 Visual studio 的程序集中的类型，复制程序集，然后粘贴在*Visual Studio 安装文件夹***\Common7\IDE\PrivateAssemblies\\**。  
  
3.  在 Visual Studio 命令提示符处，键入**devenv /rootsuffix Exp**若要打开的 Visual Studio 的实验实例。  
  
4.  在实验实例中，转到**工具 / 选项 / 环境 / 启动**页，并选择从 XAML 文件**自定义起始页**下拉列表。  
  
5.  在“视图”  菜单上，单击“起始页” 。  
  
     此时应该显示你的自定义起始页。 如果您想要更改的任何文件，必须关闭实验实例、 进行更改、 复制并粘贴已更改的文件，然后再重新打开以查看所做的更改的实验实例。  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>要应用自定义起始页中的 Visual Studio 主实例  
  
-   已测试起始页并发现它是稳定后，使用**自定义起始页**选项**选项**对话框以选择为 Visual Studio 的主实例中的起始页  
  
## <a name="see-also"></a>另请参阅  
 [演练︰ 将自定义 XAML 添加到开始页](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [将用户控件添加到开始页](../extensibility/adding-user-control-to-the-start-page.md)   
 [将 Visual Studio 命令添加到起始页](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [演练︰ 将用户设置保存在起始页上](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [部署自定义起始页](../extensibility/deploying-custom-start-pages.md)
