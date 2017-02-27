---
title: "演练: 创建基本的独立的 Shell 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell 演练"
  - "Shell [Visual Studio] 演练"
  - "演练 [Visual Studio]，隔离基于 shell 的应用程序"
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# 演练: 创建基本的独立的 Shell 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练演示如何创建独立的 shell 解决方案，自定义帮助中的关于工具窗口，并创建安装独立的 shell 的安装程序。  
  
## 系统必备  
 若要执行本演练中，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 若要部署独立的 shell，还必须使用 Visual Studio Shell \(独立\) 可再发行组件包。  
  
## 创建独立的 Shell 解决方案  
 本部分说明如何使用 Visual Studio Shell 隔离的项目模板来创建独立的 shell 解决方案。 该解决方案包含以下项目:  
  
-   *SolutionName*。AboutBoxPackage 项目，它允许您自定义帮助的 \/ 关于框中的外观。  
  
-   ShellExtensionsVSIX 项目，其中包含用于定义独立的 shell 应用程序的不同组件的源 source.extension.vsixmanifest 文件。  
  
-   *SolutionName* 项目中，它将生成调用独立的 shell 应用程序的可执行文件。 此项目包含外壳自定义设置文件夹，允许您自定义外观和独立的 shell 应用程序的行为。  
  
-   *SolutionName* UI 项目，生成的附属程序集，用于定义活动的菜单命令和可本地化的字符串。  
  
#### 若要创建基本的独立的 shell 解决方案  
  
1.  打开 Visual Studio 并创建一个新的项目。  
  
2.  在 **新项目** 窗口中，展开 **其他项目类型** 然后 **扩展性**。 选择 **Visual Studio Shell 独立** 项目模板。  
  
3.  将项目命名为 `MyVSShellStub` 并指定一个位置。 请确保 **创建解决方案的目录** 处于选中状态，，然后单击 **确定**。  
  
     新的解决方案将显示在 **解决方案资源管理器**。  
  
4.  生成解决方案并启动调试独立的 shell 应用程序。  
  
     隔离的 Visual Studio shell 将出现。 标题栏显示 **MyVSShellStub**。 标题栏图标是从 \\MyVSShellStub\\Resource Files\\ApplicationIcon.ico 生成的。  
  
## 自定义应用程序名称和图标  
 您可能想要设置你的应用程序外观的标题栏中使用的公司和其徽标的名称。 下列步骤显示如何更改名称和通过更改包定义文件，MyVSShellStub.Application.pkgdef 自定义应用程序标题栏中显示的图标。  
  
#### 若要自定义应用程序名称和图标  
  
1.  在 MyVSShellStub 项目中，打开 \\Shell Customization\\MyVSShellStub.Application.pkgdef。  
  
2.  更改 `AppName` 到的元素值 **"AppName"\="Fabrikam 音乐编辑器"**  
  
3.  若要更改的应用程序图标，将复制到 \\MyVSShellStub\\MyVSShellStub\\MyVSShellStub\\ 目录的不同的图标。 将现有的 ApplicationIcon.ico 文件重命名为 ApplicationIcon1.ico。 新的文件重命名为 ApplicationIcon.ico。  
  
4.  生成解决方案并启动调试。 独立的 shell IDE 将出现。 标题栏有新的图标旁边 **Fabrikam 音乐编辑器**。  
  
## 自定义默认 Web 浏览器主页  
 本部分说明如何更改默认主页 **Web 浏览器** 窗口是通过更改包定义文件。  
  
#### 若要自定义默认 Web 浏览器主页  
  
1.  在 MyVSShellStub.Application.pkgdef 文件中，更改 `DefaultHomePage` 到"http:\/\/www.microsoft.com"的元素值。  
  
2.  重新生成 MyVSShellStub 项目。  
  
3.  生成解决方案并启动调试。  
  
4.  在 **视图 \/ 其他窗口**, ，请单击 **Web 浏览器**。**Web 浏览器** 窗口将显示 Microsoft Corporation 主页。  
  
## 删除打印命令  
 独立的 shell 用户界面项目中的.vsct 文件包含一组窗体的声明 `<Define name=No_`*元素*`>`, ，其中 *元素* 是一种标准的 Visual Studio 菜单和命令。  
  
 如果一个声明未被注释掉，将从独立 shell 中排除该菜单或命令。 相反，如果注释声明，菜单或命令包含在独立的 shell。  
  
 在下面的步骤中，取消注释打印命令在.vsct 文件中。  
  
#### 若要删除的打印命令  
  
1.  验证 **打印** 命令出现在 **文件** 独立的 shell 应用程序菜单中。  
  
2.  在 MyVSShellStubUI 项目中，打开 \\Resource Files\\MyVSShellStubUI.vsct 以进行编辑。  
  
3.  取消注释以下行:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  这将删除打印命令。  
  
5.  开始调试独立的 shell 应用程序。 验证 **文件 \/ 打印** 命令已消失。  
  
## 从独立外壳程序删除功能  
 您可以删除某些通过编辑.pkgundef 文件，如果您不希望自定义独立的 shell 应用程序中的那些功能将随 Visual Studio 一起加载的包。 $RootKey$ \\Packages 注册表项的子项之一中指定的包。  
  
> [!NOTE]
>  若要查找的 Guid 的 Visual Studio 功能，请参阅 [Visual Studio 功能的包 Guid](../extensibility/package-guids-of-visual-studio-features.md)。  
  
 下面的过程演示如何删除 XML 编辑器与独立的 shell。  
  
#### 若要删除 XML 编辑器  
  
1.  在 MyVSShellStub 项目的外壳自定义设置文件夹中打开 MyVSShellStub.pkgundef 文件。  
  
2.  取消注释以下行:  
  
     \[$RootKey$ \\Packages\\ {87569308\-4813\-40a0\-9cd0\-d7a30838ca3f}\]  
  
3.  重新生成解决方案并启动调试独立的 shell。 打开 XML 文件，例如，\\MyVSShellStub\\MyVSShellStub\\MyVSShellStubUI\\MyVSShellStubUI.vsct。 验证文件中的 XML 关键字不颜色区分类，然后，键入"\<"在行上不会打开 XML 工具提示。  
  
## 自定义帮助 \/ 关于框  
 您可以自定义帮助\/有关框中，这将创建为独立的 shell 项目模板的一部分。  
  
#### 若要自定义公司名称  
  
1.  公司名称、 版权信息、 产品版本和产品说明 \\Properties\\AssemblyInfo.cs 文件中找到 MyVSShellStub.AboutBoxPackage 项目中。 打开此文件。  
  
2.  更改 `AssemblyCompany` 值赋给 **Fabrikam**, 、 `AssemblyProduct` 和 `AssemblyTitle` 值复制到 **Fabrikam 音乐编辑器**, ，和 `AssemblyCopyright` 值赋给 **2015 版权所有 © Fabrikam**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")] [assembly: AssemblyDescription("")] [assembly: AssemblyConfiguration("")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor ")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  若要添加该产品的说明，请更改 `AssemblyDescription` 值赋给 **Fabrikam 音乐编辑器的说明。**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  开始调试并在独立的 shell 应用程序中，打开 **帮助 \/ 关于** 框。 您应该看到已更改的字符串。 帮助的 \/ 关于框的标题是相同 `AssemblyTitle` AssemblyInfo.cs 中的值。  
  
5.  属性的 **帮助 \/ 关于** 框本身在 MyVSShellStub.AboutBoxPackage\\AboutBox.xaml 文件中找到。 若要更改帮助的 \/ 关于框的宽度，请转到 `AboutDialogStyle` 阻止并设置 `Width` 属性设置为 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window"> <Setter Property="Height" Value="Auto" /> <Setter Property="Width" Value="200" /> <Setter Property="ShowInTaskbar" Value="False" /> <Setter Property="ResizeMode" Value="NoResize" /> <Setter Property="WindowStyle" Value="SingleBorderWindow" /> <Setter Property="SizeToContent" Value="Height" /> </Style>  
    ```  
  
6.  重新生成解决方案并启动调试独立的 shell。 帮助\/有关框应为大约正方形。  
  
## 独立的 Shell 应用程序的部署之前  
 独立的 shell 应用程序可以安装在具有 Visual Studio Shell \(独立\) 可再发行组件包的任何计算机上。 有关可再发行组件包的详细信息，请参阅 [Visual Studio 扩展性下载](http://go.microsoft.com/fwlink/?LinkID=119298) 网站。  
  
## 独立的 Shell 应用程序部署  
 通过创建安装项目部署到目标计算机独立的 shell 应用程序。 您必须指定以下事项:  
  
-   文件夹和目标计算机上的文件的布局。  
  
-   保证.NET Framework 和 Visual Studio shell 运行时的启动条件是目标计算机上安装的。  
  
 在下面的过程需要在您的计算机上安装 InstallShield Limited Edition。  
  
#### 若要创建安装项目  
  
1.  在 **解决方案资源管理器**, ，用鼠标右键单击解决方案节点，然后单击 **添加新项目**。  
  
2.  在 **新项目** 对话框框中，展开 **其他项目类型** ，然后选择 **安装和部署**。 选择 InstallShield 模板。 将新项目命名为 `MySetup` ，然后单击 **确定**。  
  
3.  如果已安装 InstallShield Limited Edition，则继续下一步。  
  
     如果尚未安装 InstallShield Limited Edition，则会出现 InstallShield 下载页。 按照说明下载并安装该产品，选择符合您的 Visual Studio 版本的 InstallShield 的版本。 您必须决定是否要注册的 InstallShield 安装或将其用作评估。 安装完成后，必须重新启动 Visual Studio。  
  
    > [!IMPORTANT]
    >  在创建 InstallShield 项目之前，必须以管理员身份启动 Visual Studio。 如果不这样做，则将生成项目时出现错误。  
  
 接下来的步骤演示如何配置安装项目。  
  
> [!IMPORTANT]
>  请确保你已经配置的安装项目之前构建独立的 shell 项目的发布配置至少一次。  
  
#### 若要配置安装程序项目  
  
1.  在 **解决方案资源管理器**, 下 **MySetup** 项目中，选择 **项目助手**。 在底部的行上 **项目助手** 窗口中，选择 **应用程序信息**。 输入 **Fabrikam** 作为你的公司名称和 **Fabrikam 音乐编辑器** 作为应用程序名称。 选择的右下角的向前箭头 **项目助手**。  
  
2.  选择 **是** 下 **应用程序是否需要在计算机上安装任何软件?** ，然后选择 **Microsoft.NET Framework 4.5 Full Package**。  
  
3.  选择 **应用程序文件** 按钮在窗口的底部，然后确保 **Fabrikam 音乐编辑器** 选择文件夹。  
  
4.  选择 **将文件添加** 按钮。 在 **将文件添加** 对话框框中，添加下列文件从 **MyVSShellStub\\Release** 文件夹:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  单击 **添加项目输出** 按钮，然后添加 **MyVSShellStub\/主输出**。 单击“确定”。  
  
6.  在左窗格中，在下 **目标计算机**, ，用鼠标右键单击 **Fabrikam 音乐编辑器 \[INSTALLDIR\]** 节点，并添加 **新文件夹** 名为 **扩展**。  
  
7.  用鼠标右键单击 **扩展** 的左窗格中的节点，并添加一个名为的新文件夹 **应用程序**。  
  
8.  选择 **应用程序** 文件夹，然后单击 **添加项目输出** 按钮，然后从 MyVSShellStub.AboutBoxPackage 项目中选择的主输出。  
  
9. 单击 **将文件添加** 按钮，然后从 \\MyVSShellStub\\Release\\Extensions\\Application\\ 文件夹添加以下文件:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. 用鼠标右键单击 **Fabrikam 音乐编辑器 \[INSTALLDIR\]** 的左窗格中的节点，并添加一个名为的新文件夹 **1033年**。  
  
11. 选择 1033年文件夹，然后单击 **添加项目输出** 按钮，然后从 MyVSShellStubUI 项目选择的主输出。  
  
12. 将移动到 **应用程序快捷方式** 窗口。  
  
13. 单击 **新建** 来创建一个快捷方式并选择 **\[ProgramFilesFolder\] \\Fabrikam\\Fabrikam Music Editor\\MyVSShellStub.Primary Output**。  
  
14. 将移动到 **安装访谈** 窗格。  
  
15. 将所有项目都设为 **否**。  
  
16. 在 **解决方案资源管理器**, ，在 MySetup 项目中，打开 **定义安装程序要求和操作 \\ 要求**。**要求** 窗口随即打开。  
  
17. 右键单击 **系统软件要求** ，然后选择 **创建新的启动条件**。**系统搜索向导** 出现。  
  
18. 在 **要查找什么?** 窗格中，选择 **注册表项** 在下拉列表中，单击 **下一步**。  
  
19. 在 **要方式查找它?** 窗格中，选择 **HKEY\_LOCAL\_MACHINE** 作为的注册表根目录。 输入 **SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** 对于 64 位系统或 **SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** 对于 32 位系统，然后输入 **安装** 作为该注册表值。 单击“下一步”。  
  
20. 在 **您想要的值执行的操作?** 窗格中，输入 **本产品需要 Visual Studio 2015 独立 Shell 可再发行的安装。** 作为显示文本，然后单击 **完成**。  
  
21. 重新生成独立的 shell 解决方案，以创建安装项目。  
  
     您可以在以下文件夹中找到 setup.exe 文件:  
  
     \\MyVSShellStub\\MySetup\\MySetup\\Express\\SingleImage\\DiskImages\\DISK1  
  
## 测试安装程序  
 要测试安装程序，请将 setup.exe 文件复制到另一台计算机并运行安装程序可执行文件。 您应能够运行独立的 shell 应用程序。