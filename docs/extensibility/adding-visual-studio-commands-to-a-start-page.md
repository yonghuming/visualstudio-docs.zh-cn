---
title: "将 Visual Studio 命令添加到起始页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 973e0cfbceb6cbf67c5bc11cdde370607334809a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>将 Visual Studio 命令添加到起始页
当创建自定义起始页时，你可以向其添加 Visual Studio 命令。 本文档讨论的不同方式，将 Visual Studio 命令绑定到在起始页上的 XAML 对象。  
  
 有关在 XAML 中的命令的详细信息，请参阅[命令概述](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>也从该命令添加命令  
 开始页中创建[创建自定义起始页](../extensibility/creating-a-custom-start-page.md)添加<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>和<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>命名空间，如下所示。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 从程序集 Microsoft.VisualStudio.Shell.Immutable.11.0.dll 为 Microsoft.VisualStudio.Shell 添加另一个命名空间。 （你可能需要在你的项目中添加此程序集的引用。）  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 你可以使用`vscom:`页上，通过设置控件绑定到 XAML 的 Visual Studio 命令别名<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>该控件的属性`vscom:VSCommands.ExecuteCommand`。 然后，可以设置<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>属性设置为要执行，如下面的示例中所示的命令的名称。  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:`别名，它是指 XAML 架构，是必需的所有命令的开头。  
  
 你可以设置的值`Command`属性设置为从可以访问任何命令**命令**窗口。 有关可用命令的列表，请参阅[Visual Studio 命令别名](../ide/reference/visual-studio-command-aliases.md)。  
  
 如果要添加的命令需要一个附加参数，可以将其添加到的值`CommandParameter`属性。 从使用空格，如下面的示例中所示的命令的单独参数。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>也从该命令中调用扩展  
 你可以使用相同的语法，用于调用其他 Visual Studio 命令，从已注册 Vspackage 调用命令。 例如，如果已安装的 VSPackage 添加**主页**命令**视图**菜单上，你可以通过设置调用该命令`CommandParameter`到`View.HomePage`。  
  
> [!NOTE]
>  如果调用 VSPackage 与关联的命令，在调用命令时，必须加载包。  
  
## <a name="adding-commands-from-assemblies"></a>从程序集添加命令  
 若要从一个程序集，或访问代码在 VSPackage 所关联的菜单命令，请调用命令，必须为程序集创建别名，然后调用别名。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>若要从程序集调用命令  
  
1.  在解决方案中，添加对程序集的引用。  
  
2.  在 StartPage.xaml 文件的顶部，添加的命名空间指令对于程序集，如下面的示例中所示。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  调用此命令的设置`Command`的 XAML 对象，如下面的示例中所示的属性。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  必须将程序集复制，然后将其在粘贴...\\ *Visual Studio 安装文件夹*\Common7\IDE\PrivateAssemblies\ 若要确保加载之前调用。  
  
## <a name="adding-commands-with-the-dte-object"></a>将命令添加与 DTE 对象  
 在从起始页，在标记和代码中，可以访问 DTE 对象。  
  
 在标记中，你可以通过访问该[绑定标记扩展](/dotnet/framework/wpf/advanced/binding-markup-extension)语法来调用<xref:EnvDTE.DTE>对象。 您可以使用此方法将绑定到简单属性，例如那些返回集合，但无法绑定到方法或服务。 下面的示例演示<xref:System.Windows.Controls.TextBlock>绑定到控件<xref:EnvDTE._DTE.Name%2A>属性，和一个<xref:System.Windows.Controls.ListBox>枚举的控件<xref:EnvDTE.Window.Caption%2A>返回的集合的属性<xref:EnvDTE._DTE.Windows%2A>属性。  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 有关示例，请参阅[演练： 起始页上保存用户设置](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)。  
  
## <a name="see-also"></a>另请参阅  
 [将用户控件添加到起始页](../extensibility/adding-user-control-to-the-start-page.md)