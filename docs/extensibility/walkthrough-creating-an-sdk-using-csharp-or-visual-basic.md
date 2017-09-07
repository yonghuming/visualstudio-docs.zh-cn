---
title: "演练： 创建使用 C# 或 Visual Basic 的 SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 20
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
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: d40de5bedbb0e77aee2a0dbed34f8dc22d3835c9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>演练： 创建使用 C# 或 Visual Basic 的 SDK
在本演练中，你将了解如何通过使用 Visual C# 创建一个简单的数学库 SDK 并然后打包 SDK 作为 Visual Studio 扩展 (VSIX)。 你将完成以下过程：  
  
-   [若要创建 SimpleMath Windows 运行时组件](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [若要创建 SimpleMathVSIX 扩展项目](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [若要创建的示例应用程序使用类库](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>先决条件  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="createClassLibrary"></a>若要创建 SimpleMath Windows 运行时组件  
  
1.  在菜单栏上，选择**文件**，**新建**，**新项目**。  
  
2.  在模板列表中，展开**Visual C#**或**Visual Basic**，选择**Windows 应用商店**节点，然后选择**Windows 运行时组件**模板。  
  
3.  在**名称**框中，指定**SimpleMath**，然后选择**确定**按钮。  
  
4.  在**解决方案资源管理器**，打开快捷菜单**SimpleMath**项目节点，，然后选择**属性**。  
  
5.  重命名**Class1.cs**到**Arithmetic.cs**和将其更新为匹配下面的代码：  
  
     [!code-csharp[CreatingAnSDKUsingWinRT #3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)][!code-vb[CreatingAnSDKUsingWinRT #3  ](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  在**解决方案资源管理器**，打开快捷菜单**解决方案 SimpleMath**节点，然后选择**Configuration Manager**。  
  
     **Configuration Manager**对话框随即打开。  
  
7.  在**活动解决方案配置**列表中，选择**版本**。  
  
8.  在**配置**列中，验证**SimpleMath**该行被设置为**版本**，然后选择**关闭**按钮以接受更改。  
  
    > [!IMPORTANT]
    >  SDK for SimpleMath 组件包括只有一个配置。 此配置必须是发布版本中，或使用该组件的应用不会传递证书颁发[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]。  
  
9. 在**解决方案资源管理器**，打开快捷菜单**SimpleMath**项目节点，，然后选择**生成**。  
  
##  <a name="createVSIX"></a>若要创建 SimpleMathVSIX 扩展项目  
  
1.  上的快捷菜单**解决方案 SimpleMath**节点，选择**添加**，**新项目**。  
  
2.  在模板列表中，展开**Visual C#**或**Visual Basic**，选择**扩展性**节点，然后选择**VSIX 项目**模板。  
  
3.  在**名称**框中，指定**SimpleMathVSIX**，然后选择**确定**按钮。  
  
4.  在**解决方案资源管理器**，选择**source.extension.vsixmanifest**项。  
  
5.  在菜单栏上，依次选择 **“视图”**、 **“代码”**。  
  
6.  用下列 XML 替换现有的 XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT # 1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  在**解决方案资源管理器**，选择**SimpleMathVSIX**项目。  
  
8.  在菜单栏上，选择**项目**，**添加新项**。  
  
9. 在列表中**通用项**，展开**数据**，然后选择**XML 文件**。  
  
10. 在**名称**框中，指定`SDKManifest.xml`，然后选择**添加**按钮。  
  
11. 在**解决方案资源管理器**，打开快捷菜单`SDKManifest.xml`，选择**属性**，然后将更改的值**包括在 VSIX 中的**属性**True**。  
  
12. 用下列 XML 替换该文件的内容：  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. 在**解决方案资源管理器**，打开快捷菜单**SimpleMathVSIX**项目，选择**添加**，然后选择**新文件夹**。  
  
14. 重命名该文件夹以`references`。  
  
15. 打开的快捷菜单**引用**文件夹中，选择**添加**，然后选择**新文件夹**。  
  
16. 重命名子文件夹`commonconfiguration`、 创建在其中，一个子文件夹和子文件夹命名为`neutral`。  
  
17. 重复上述四个步骤中，这一次重命名为第一个文件夹`redist`。  
  
     项目现在包含以下文件夹结构：  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. 在**解决方案资源管理器**，打开快捷菜单**SimpleMath**项目，，然后选择**在文件资源管理器中打开文件夹**。  
  
19. 在**文件资源管理器**，导航到 bin\Release 文件夹、 打开 SimpleMath.winmd，为文件的快捷菜单，然后选择**复制**。  
  
20. 在**解决方案资源管理器**，将文件粘贴到 references\commonconfiguration\neutral 文件夹**SimpleMathVSIX**项目。  
  
21. 重复上述步骤，将 SimpleMath.pri 文件粘贴到 redist\commonconfiguration\neutral 文件夹**SimpleMathVSIX**项目。  
  
22. 在**解决方案资源管理器**，选择**SimpleMath.winmd**。  
  
23. 在菜单栏上，选择**视图**，**属性**(键盘： 按 F4 键)。  
  
24. 在**属性**窗口中，更改**生成操作**属性**内容**，然后将更改**包括在 VSIX 中的**属性**True**。  
  
25. 在**解决方案资源管理器**，重复此流程的**SimpleMath.pri**。  
  
26. 在**解决方案资源管理器**，选择**SimpleMathVSIX**项目。  
  
27. 在菜单栏上，选择**生成**，**生成 SimpleMathVSIX**。  
  
28. 在**解决方案资源管理器**，打开快捷菜单**SimpleMathVSIX**项目，，然后选择**在文件资源管理器中打开文件夹**。  
  
29. 在**文件资源管理器**，导航到 \bin\Release 文件夹，然后运行 SimpleMathVSIX.vsix 来进行安装。  
  
30. 选择**安装**按钮，等待安装完成，然后再重新启动 Visual Studio。  
  
##  <a name="createSample"></a>若要创建的示例应用程序使用类库  
  
1.  在菜单栏上，选择**文件**，**新建**，**新项目**。  
  
2.  在模板列表中，展开**Visual C#**或**Visual Basic**，然后选择**Windows 应用商店**节点。  
  
3.  选择**空白应用程序**模板，将项目**ArithmeticUI**，然后选择**确定**按钮。  
  
4.  在**解决方案资源管理器**，打开快捷菜单**ArithmeticUI**项目，，然后选择**添加**，**引用**。  
  
5.  在引用类型的列表中，展开**Windows**，然后选择**扩展**。  
  
6.  在详细信息窗格中，选择**简单数学 SDK**扩展。  
  
     有关 SDK 的其他信息将出现。 你可以选择**更多信息**链接以打开 http://www.msdn.microsoft.com，如你在本演练前面部分的 SDKManifest.xml 文件中指定。  
  
7.  在**引用管理器**对话框中，选择**简单数学 SDK**复选框，然后依次**确定**按钮。  
  
8.  在菜单栏上，选择**视图**，**对象浏览器**。  
  
9. 在**浏览**列表中，选择**简单数学**。  
  
     你现在可以浏览什么是 SDK 中。  
  
10. 在**解决方案资源管理器**，打开 MainPage.xaml，并将其内容替换下面的 XAML:  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
    
    **Visual Basic**
    ```xml
    <Page
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
  
11. 更新 MainPage.xaml.cs 以将匹配下面的代码：  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp #2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)][!code-vb[CreatingAnSDKUsingWinRTDemoApp #2  ](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. 选择 F5 键以运行应用程序。  
  
13. 在应用中，输入任何两个数字，选择某一操作，，然后选择 **=** 按钮。  
  
     将显示正确的结果。  
  
 已成功创建并使用扩展 SDK。  
  
## <a name="see-also"></a>另请参阅  
 [演练： 创建使用 c + + 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [演练： 创建使用 JavaScript SDK](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [获取软件开发工具包](../extensibility/creating-a-software-development-kit.md)
