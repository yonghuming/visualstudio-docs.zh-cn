---
title: "起始页最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "起始页提示"
  - "起始页最佳做法"
  - "起始页设计"
ms.assetid: f6ce1ce0-746e-4004-a37f-6f176f6f5851
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 起始页最佳做法
由于起始页可以访问 Visual Studio 命令，而且会在 Visual Studio 加载时打开，我们建议你在使用它或将其分发之前，确保任何自定义起始页的稳定性。 本主题提供可靠起始页设计的最佳做法，并包括有关如何创建有帮助用户界面 \(UI\) 的指南。  
  
## 稳定性指南  
  
### 资源可用性  
 制作可靠自定义起始页中最重要的注意事项是确保所有必需资源均可用：  
  
-   已安装所有必需的软件包。  
  
-   预加载软件包。  
  
-   所有必需的程序集都在 \\PrivateAssemblies\\ 文件夹中。  
  
-   每个使用网络或 Internet 连接的组件都有用于脱机方案和连接断开的备用路径。  
  
### 性能  
 如果起始页有较大内存需求或加载多个资源，请考虑启动性能会受到怎样的影响。 对此类起始页进行编程以按需加载组件，或在后台加载（如果可行），以便不会显著增加启动时间。  
  
### 开发过程  
 如果你直接修改活动起始页，可能无意中引发错误，导致 Visual Studio 崩溃。 由于每次 Visual Studio 打开时都将打开起始页，因此很难修复崩溃的起始页。 因此，我们建议你修改起始页文件的副本，并在 Visual Studio 实验实例中对其进行测试，提高可靠性。 当新的起始页稳定时，可以将其设置在 Visual Studio 主实例中运行。  
  
> [!NOTE]
>  你在主实例中使用任一第三方起始页之前，我们还建议先在 Visual Studio 的实验实例中测试它。  
  
##### 在 Visual Studio 的实验实例中测试起始页  
  
1.  如果你正在使用起始页项目模板，请按 F5。 否则：  
  
    1.  将 .xaml 文件和任何支持文本或标记复制到 \\%USERPROFILE%\\My Documents\\Visual Studio *\<版本\>*\\StartPages\\。  
  
    2.  将任何所需程序集复制到 *\<Visual Studio 安装路径\>*\\Common7\\IDE\\PrivateAssemblies\\。  
  
    3.  通过在 Visual Studio 命令提示符中使用以下命令打开 Visual Studio 的实验实例。  
  
         **Devenv \/rootsuffix exp**  
  
2.  在**“工具”**菜单上，单击**“选项”**。 选择“环境”，然后选择“启动”。 在“自定义起始页”列表中，选择重命名的 StartPage.xaml 文件，然后单击“确定”。  
  
3.  在“视图”菜单上，单击“起始页”。  
  
     自定义起始页将打开。 如果你正修改的起始页崩溃，可以重新启动 Visual Studio 的主实例，进行所需的修复，然后打开另一个实验实例，以继续修改自定义起始页。  
  
 如果你的起始页导致 Visual Studio 的主实例崩溃，可将 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\CustomizationEnabled 的注册表值设置为 0 来暂时禁用自定义起始页。 或者，可将当前的默认起始页暂时重命名为 .xaml 文件。 任一方法都可让你打开 Visual Studio 并有足够时间修复错误。  
  
### 调试  
 当首次加载起始页时，起始页工具窗口会捕获异常，但之后将不再捕获异常。 可将以下注册表值设置为“1”来通知 Visual Studio 显示所有未处理的异常。  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\General\\EnableUnhandledExceptionDisplay  
  
 异常信息将在消息框中显示，从而使你可以在起始页上、在其他未处理的位置中、甚至在 Visual Studio 主实例中调试控件。 如果在异常产生后不能进行调试，你可以使用“devenv \/safemode”命令重新启动 Visual Studio，切换回以前的起始页，然后继续在实验实例中调试。  
  
### 相对路径  
 在从起始页引用文件路径时，始终使用相对路径以允许不同的系统配置。 但是，起始页上所有相对路径的根并不解析 \\StartPages\\ 文件夹而解析 ..\\*Visual Studio 安装文件夹*\\Common7\\IDE，devenv.exe 就位于此处。 若要设置相对于 \\StartPages\\ 文件夹的路径，使用 VS 起始页相对转换器。 通过将对象的 `Source` 属性设置为 `vs:StartPageRelative` 实现此操作，如下面的示例所示。  
  
 XAML  
  
```  
<Image Source="{vs:StartPageRelative myImage.png}" .../>  
```  
  
 访问 Visual Studio 所含的资源或其他包所含的文件时，使用标准的相对路径语法。  
  
### 部署  
 当为其他用户部署自定义起始页时，我们建议使用下列的最佳做法。  
  
#### 用户设置  
  
-   尊重用户设置。 不要覆盖现有的起始页首选项。  
  
#### VSIX  
 这些做法适用于 VSIX 部署：  
  
-   使用 VSIX 清单中的 [GettingStartedGuide](http://msdn.microsoft.com/zh-cn/261bb1fd-abae-4ed6-80a8-90d5fc3bb8c6) 元素以指向有关如何设置默认起始页的说明。  
  
-   使用 VSIX 清单的 [Name](http://msdn.microsoft.com/zh-cn/d99d38d1-060b-401a-9b9f-ede2c6213a11) 元素和 [Description](http://msdn.microsoft.com/zh-cn/24ddc57e-e991-4a43-b0c9-0e76da293e99) 元素以将扩展明确标识为起始页，并描述其用途。  
  
-   验证你的 VSIX 清单是否不含绝对路径。  
  
-   当你上载到 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)网站，应包含相关标记，以便用户能将扩展标识为起始页。  
  
#### MSI  
 如果你生成起始页作为正在 Windows Installer \(MSI\) 中部署的较大扩展的一部分，则可设置起始页为在目标计算机上安装的默认起始页。 若要完成此操作，将起始页 .xaml 文件的名称写入此注册表项的 Uri 值：HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\。 设置此注册表值时使用以下指南：  
  
-   在安装程序中，提供 UI 让用户选择是否要将新的起始页设置为默认起始页。  
  
-   如果用户卸载你的扩展，请还原以前的注册表值。  
  
### Windows Presentation Foundation \(WPF\)  
 XAML 标记应遵循 WPF 最佳做法。 有关用于应用程序开发的 [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] 和 [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] 最佳做法的信息，请根据需要参阅下面的主题。  
  
|区域|主题|  
|--------|--------|  
|可访问性|[Accessibility Best Practices](../Topic/Accessibility%20Best%20Practices.md)|  
|本地化|[WPF 全球化和本地化概述](../Topic/WPF%20Globalization%20and%20Localization%20Overview.md)|  
|性能|[优化 WPF 应用程序性能](../Topic/Optimizing%20WPF%20Application%20Performance.md)|  
|安全性|[安全性 \(WPF\)](../Topic/Security%20\(WPF\).md)|  
  
## 用户界面指南  
 若要确保方便和直观的起始页用户体验，请在适用时使用以下 UI 指南。  
  
### 首行  
  
#### 横幅  
  
-   使横幅图像的高度与它所在行的行定义高度相同。  
  
-   若要适应不同的窗口大小和屏幕分辨率，则使横幅图像在任何宽度都有较好的视觉效果。  
  
-   保持横幅的整洁。 不要用其他按钮或图形覆盖徽标。  
  
### 左列  
  
#### 按钮区域  
  
-   只将最常用的控件放入按钮区域，以便为要显示的最近项目名称留出空间。 我们建议按钮数少于五个。  
  
#### 最近项目  
  
-   此控件允许用户访问最近的项目。 可将要显示的项目数设置为 0 到 24。 由于这是起始页中使用频率最高的部分，我们建议不要将它删除。  
  
#### 起始页选项  
  
-   请确保“项目加载后关闭此页”和“启动时显示此页”选项在起始页上出现。  
  
-   对于此区域中的其他控件，我们建议你使用复选框或单选按钮，并确保这些控件与起始页首选项关联。  
  
### 内容区域  
  
#### 顶级选项卡  
  
-   在典型的屏幕宽度中避免添加过多选项卡而使选项卡控件换行。  
  
-   为选项卡使用较短的描述性名称。  
  
-   请确保选项卡表示分组的内容区域。  
  
#### 子级别选项卡  
  
-   如果你有两个以上的副标题，则只使用子级别导航。  
  
-   在典型的屏幕宽度中避免添加过多选项卡而使选项卡控件换行。  
  
-   为选项卡使用较短的描述性名称。  
  
#### 子级别选项卡内容  
  
-   在子级别选项卡上显示不超过五个的内容项。  
  
#### 项内容  
  
-   每个内容项显示不超过四个的链接。  
  
-   如果你将图像与内容项关联，请确保每个图像都是 125x175 像素。  
  
-   为内容项使用较短的描述性标题。  
  
-   将内容项的说明限制为两句或更少。  
  
### 常规  
  
#### 动画  
  
-   如果使用动画，将它们限制为 0.5 秒或更少以帮助防止出现劣质效果。  
  
#### 环境颜色  
  
-   遵照字体和颜色的系统设置。  
  
-   使用浅色背景。  
  
-   使用远程桌面检测，确保远程会话中的颜色淡化正常。  
  
## 请参阅  
 [起始页体系结构](/visual-cpp/misc/start-page-architecture)   
 [部署自定义起始页](../extensibility/deploying-custom-start-pages.md)   
 [将 Visual Studio 命令添加到起始页](../extensibility/adding-visual-studio-commands-to-a-start-page.md)