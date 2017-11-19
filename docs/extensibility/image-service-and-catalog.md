---
title: "映像服务和目录 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5813788834a7a5a99c10fe6dafc35a300bac007
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="image-service-and-catalog"></a>映像服务和目录
此指南包含指导和采用 Visual Studio 映像服务和 Visual Studio 2015 中引入的映像目录的最佳做法。  
  
 在 Visual Studio 2015 中引入的映像服务允许开发人员获取的最佳图像设备和用户的选择的主题，以显示映像，包括有关所显示的上下文的正确主题。 采用映像服务将帮助消除与资产维护、 HDPI 扩展，和主题相关的主要难题。  
  
|||  
|-|-|  
|**今天问题**|**解决方案**|  
|背景色混合|内置的 alpha 混合|  
|主题 （某些） 映像|主题元数据|  
|高对比度模式|备用高对比度资源|  
|需要多个资源来不同 DPI 模式|可选择资源，基于矢量的备用方案|  
|重复的图像|每个图像概念的一个标识符|  
  
 为何采用映像服务？  
  
-   始终从 Visual Studio 中获取最新的"像素完美"映像  
  
-   你可以提交并使用你自己的映像  
  
-   无需测试出 Windows 添加新 DPI 缩放图像  
  
-   地址实现中的旧体系结构障碍  
  
 Visual Studio shell 工具栏之前和之后使用映像服务：  
  
 ![图像服务前后](../extensibility/media/image-service-before-and-after.png "图像服务前后")  
  
## <a name="how-it-works"></a>它是如何工作  
 映像服务可以提供适用于任何支持的 UI 框架的位图化映像：  
  
-   WPF: BitmapSource  
  
-   WinForms: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 图像服务流关系图  
  
 ![图像服务流关系图](../extensibility/media/image-service-flow-diagram.png "图像服务流关系图")  
  
 **映像名字对象**  
  
 图像名字对象 （或简称名字对象） 是 GUID/ID 对唯一标识的图像资产或映像库中的图像列表资产。  
  
 **已知的名字对象**  
  
 按任何 Visual Studio 组件或扩展的 Visual Studio 映像目录和公开使用耗材中包含的图像名字对象的组。  
  
 **图像清单文件**  
  
 图像清单 (.imagemanifest) 文件是定义一组的图像资产，表示这些资产的实际图像或表示每个资产的映像的名字对象的 XML 文件。 图像的清单可以定义独立图像或图像列表以支持旧版 UI。 此外，还有可以进行设置的资产上或在每个资产后面的单独映像来更改何时以及如何显示这些资产的属性。  
  
 **图像清单架构**  
  
 完成映像清单如下所示：  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Import, Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **符号**  
  
 如提高可读性并维护帮助，则图像清单可以使用特性值的符号。 符号定义如下：  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**子元素**|**定义**|  
|导入|导入当前清单中使用的给定清单文件的符号|  
|Guid|符号表示一个 GUID，并且必须与匹配 GUID 的格式设置|  
|Id|符号表示 ID 和必须为非负整数|  
|字符串|符号表示任意字符串值|  
  
 符号是区分大小写，并引用使用 $(symbol-name) 语法：  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 为所有清单预定义了某些符号。 这些绑定可以使用的 Uri 特性中\<源 > 或\<导入 > 到本地计算机上的引用路径的元素。  
  
|||  
|-|-|  
|**符号**|**描述**|  
|CommonProgramFiles|%Commonprogramfiles%环境变量的值|  
|LocalAppData|%Localappdata%环境变量的值|  
|ManifestFolder|包含清单的文件的文件夹|  
|我的文档|当前用户的我的文档文件夹的完整路径|  
|ProgramFiles|%Programfiles%环境变量的值|  
|系统|Windows\System32 文件夹|  
|WinDir|%Windir%环境变量的值|  
  
 **Image**  
  
 \<映像 > 元素定义可由标记引用的映像。 GUID 和 ID 综上所述窗体的图像标记。 为图像标记必须是唯一的整个图像库。 如果多个映像具有给定名字对象，生成库时遇到的第一个是保留的一个。  
  
 它必须包含至少一个源。 非特定大小源将为获得最佳结果提供广泛的大小，但这些内容并非必需。 如果服务要求中未定义的大小的图像\<映像 > 元素和没有任何非特定于大小的源，则服务将选择最佳的大小特定源并将其缩放到所请求的大小。  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**特性**|**定义**|  
|Guid|[必需]映像名字对象的 GUID 部分|  
|Id|[必需]图像标记 ID 部分|  
|AllowColorInversion|[可选的默认为 true]指示映像是否可以有在深色背景上使用时以编程方式反转其颜色。|  
  
 **源**  
  
 \<源 > 元素定义单个映像源资产 （XAML 和 PNG）。  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**特性**|**定义**|  
|URI|[必需]一个 URI，定义可以从加载映像的位置。 它可以是以下项之一：<br /><br /> -A[包 URI](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx)使用应用程序: / / 机构<br />-An 绝对组件资源引用<br />的包含本机资源的文件路径|  
|背景|[可选]指示什么类型的后台源旨在一起使用。<br /><br /> 它可以是以下项之一：<br /><br /> *Light:*可以在浅色背景上使用了源。<br /><br /> *深色：*可以深背景上使用了源。<br /><br /> *高对比度：*可以在高对比度模式中的任何背景上使用了源。<br /><br /> *HighContrastLight:*可以在高对比度模式中浅色背景上使用了源。<br /><br /> *HighContrastDark:*可以深在高对比度模式中背景上使用了源。<br /><br /> 如果省略背景特性，则可以在任何背景上使用源。<br /><br /> 如果后台*Light*，*深色*， *HighContrastLight*，或*HighContrastDark*，永远不会反转的源的颜色。 如果省略背景或将其设置为*高对比度*，由图像的控制的源的颜色反转**AllowColorInversion**属性。|  
|||  
  
 A\<源 > 元素可以具有完全的以下的可选子元素之一：  
  
||||  
|-|-|-|  
|**元素**|**属性 （所有所需）**|**定义**|  
|\<大小 >|值|源将用于给定的大小 （以设备为单位） 的映像。 图像将正方形。|  
|\<SizeRange >|MinSize，最大大小|源将可用于映像从 MinSize 到最大大小 （以设备为单位） （含）。 图像将正方形。|  
|\<维度 >|宽度、 高度|源将用于给定的宽度和高度 （以设备为单位） 的映像。|  
|\<DimensionRange >|MinWidth，MinHeight，<br /><br /> MaxWidth MaxHeight|源将用于从最小宽度/高度最大宽度/高度 （以设备为单位） 的映像 （含）。|  
  
 A\<源 > 元素可能还包含一个可选\<NativeResource > 子元素，它定义\<源 >，从本机程序集，而不是托管程序集加载。  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**特性**|**定义**|  
|类型|[必需]本机资源，XAML 或 PNG 的类型|  
|Id|[必需]本机资源的整数 ID 部分|  
  
 **ImageList**  
  
 \<ImageList > 元素定义一个可以在单个的条带中返回的映像的集合。 根据需要将点播情况下，生成的条带。  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**特性**|**定义**|  
|Guid|[必需]映像名字对象的 GUID 部分|  
|Id|[必需]图像标记 ID 部分|  
|外部|[可选的默认为 false]指示映像名字对象是否引用当前清单中的图像。|  
  
 包含映像的名字对象没有以引用当前的清单中定义的映像。 如果在映像库中找不到包含的图像，则将在该处使用空白占位符图像。  
  
## <a name="using-the-image-service"></a>使用映像服务  
  
### <a name="first-steps-managed"></a>第一个步骤 （托管）  
 若要使用映像服务，你需要将对某些或所有以下程序集的引用添加到你的项目：  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   如果你使用内置映像目录 KnownMonikers 被必需的  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   如果你使用是必需的**CrispImage**和**ImageThemingUtilities** WPF UI 所示  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   如果你使用是必需的**ImageMoniker**和**ImageAttributes**类型  
  
    -   **EmbedInteropTypes**应设置为 true  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   如果你使用是必需的**IVsImageService2**类型  
  
    -   **EmbedInteropTypes**应设置为 true  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   如果你使用是必需的**BrushToColorConverter**为 ImageThemingUtilities。**ImageBackgroundColor** WPF UI 所示  
  
-   **Microsoft.VisualStudio.Shell。\<VSVersion >.0**  
  
    -   如果你使用是必需的**IVsUIObject**类型  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   如果你使用的 WinForms 相关的 UI 帮助器被必需的  
  
    -   **EmbedInteropTypes**应设置为 true  
  
### <a name="first-steps-native"></a>第一个步骤 （本机）  
 若要使用映像服务，你需要包含部分或全部到你的项目的以下标头：  
  
-   **KnownImageIds.h**  
  
    -   如果你使用内置映像目录是必需的**KnownMonikers**，但不能使用**ImageMoniker**类型，如中返回的值**IVsHierarchy GetGuidProperty**或**GetProperty**调用。  
  
-   **KnownMonikers.h**  
  
    -   如果你使用内置映像目录是必需的**KnownMonikers**。  
  
-   **ImageParameters140.h**  
  
    -   如果你使用是必需的**ImageMoniker**和**ImageAttributes**类型。  
  
-   **VSShell140.h**  
  
    -   如果你使用是必需的**IVsImageService2**类型。  
  
-   **ImageThemingUtilities.h**  
  
    -   所需如果你将无法使映像服务为你处理主题。  
  
    -   不要使用此标头，如果映像服务可以处理映像主题。  
  
-   **VSUIDPIHelper.h**  
  
    -   如果使用的 DPI 帮助器以获取当前 DPI 必需。  
  
## <a name="how-do-i-write-new-wpf-ui"></a>如何编写新的 WPF UI？  
  
1.  通过添加在上面所需的程序集引用的开始到你的项目开始步骤部分。 你不必添加它们的所有，因此添加所需的引用。 (注意： 如果你使用，或者有权访问**颜色**而不是**画笔**，则可以跳到引用**实用工具**，因为你不需要将转换器。)  
  
2.  选择所需的映像，获取其名字对象。 使用**KnownMoniker**，或使用你自己，如果你有自己的自定义映像和名字对象。  
  
3.  添加**CrispImages**到你的 XAML。 （请参阅下面的示例）。  
  
4.  设置**ImageThemingUtilities.ImageBackgroundColor** UI 层次结构中的属性。 (此属性应设置在其中的背景色已知的不一定是在位置**CrispImage**。)（请参阅下面的示例）。  
  
```xaml  
<Window  
  x:Class="WpfApplication.MainWindow"  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"  
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">  
  <Window.Resources>  
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>  
  </Window.Resources>  
  <StackPanel Background="White" VerticalAlignment="Center"   
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">  
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />  
  </StackPanel>  
</Window>  
```  
  
 **如何更新现有 WPF UI？**  
  
 更新现有 WPF UI 是一个相对简单的过程包含三个基本步骤：  
  
1.  全部替换\<映像 > 中与你的 UI 元素\<CrispImage > 元素  
  
2.  将源的所有属性都更改为名字对象属性  
  
    -   如果图像将永远不会更改，并且使用**KnownMonikers**，然后以静态方式将绑定到该属性**KnownMoniker**。 （请参阅上面的示例。）  
  
    -   如果图像将永远不会更改，并且使用你自己的自定义映像，然后以静态方式将绑定到您自己的名字对象。  
  
    -   如果可以更改该映像，将名字对象属性绑定到一个代码属性，将属性更改通知。  
  
3.  某个位置在 UI 层次结构中，设置**ImageThemingUtilities.ImageBackgroundColor**以便确保颜色反转能否正常工作。  
  
    -   这可能需要使用**BrushToColorConverter**类。 （请参阅上面的示例。）  
  
## <a name="how-do-i-update-win32-ui"></a>如何更新 Win32 UI？  
 将以下代码添加到你的代码在适当的替换原始加载的映像。 切换用于返回而不是与 HIMAGELIST HICONs HBITMAPs，根据需要的值。  
  
 **获取映像服务**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **请求映像**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>如何更新 WinForms UI？  
 将以下代码添加到你的代码在适当的替换原始加载的映像。 切换用于返回与图标的位图，根据需要的值。  
  
 **使用语句给出帮助信息**  
  
```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **获取映像服务**  
  
```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **请求映像**  
  
```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>如何在新的工具窗口中使用映像名字对象？  
 VSIX 包项目模板已更新为 Visual Studio 2015。 若要创建新的工具窗口，右键单击 VSIX 项目，然后选择"添加新项..."(Ctrl + Shift + A)。 在项目语言扩展性节点中，选择"自定义工具窗口中，"为工具窗口中提供一个名称，然后按"添加"按钮。  
  
 这些是要在工具窗口中使用名字对象的键位置。 按照每个的说明：  
  
1.  工具窗口选项卡当选项卡获取小足够 （也在 Ctrl + Tab 窗口切换器中使用）。  
  
     为派生自的类的构造函数添加以下行**ToolWindowPane**类型：  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  该命令来打开工具窗口。  
  
     在.vsct 文件包中，编辑工具窗口的命令按钮：  
  
    ```xml  
    <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <!-- Replace this KnownMoniker with your desired ImageMoniker -->  
      <Icon guid="ImageCatalogGuid" id="Blank" />  
      <!-- Add this -->  
      <CommandFlag>IconIsMoniker</CommandFlag>  
      <Strings>  
        <ButtonText>MyToolWindow</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
 **如何在现有的工具窗口中使用映像名字对象？**  
  
 更新现有的工具窗口用于映像名字对象是与用于创建新的工具窗口的步骤类似。  
  
 这些是要在工具窗口中使用名字对象的键位置。 按照每个的说明：  
  
1.  工具窗口选项卡当选项卡获取小足够 （也在 Ctrl + Tab 窗口切换器中使用）。  
  
    1.  派生自的类的构造函数中删除这些行 （如果存在） **ToolWindowPane**类型：  
  
        ```csharp  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  请参阅步骤 #1 的"如何实现新工具窗口中的使用映像名字对象？" 上面的部分。  
  
2.  该命令来打开工具窗口。  
  
    -   请参阅步骤 #2 的"如何实现新工具窗口中的使用映像名字对象？" 上面的部分。  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>如何在.vsct 文件中使用映像名字对象？  
 更新.vsct 文件，如下面的注释行所示：  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we're using the Guid for the VS image catalog.  
             Change the id attribute to be the ID of the desired image moniker. -->  
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <CommandFlag>DefaultInvisible</CommandFlag>  
        <CommandFlag>DefaultDisabled</CommandFlag>  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>IconAndText</CommandFlag>  
        <!-- Add the IconIsMoniker CommandFlag -->  
        <CommandFlag>IconIsMoniker</CommandFlag>  
        <Strings>  
          <ButtonText>Quick Fixes...</ButtonText>  
          <CommandName>Show Quick Fixes</CommandName>  
          <CanonicalName>ShowQuickFixes</CanonicalName>  
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>  
        </Strings>  
      </Button>  
    </Buttons>  
  </Commands>  
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->  
  <Symbols>  
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />  
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">  
      <IDSymbol name="cmdidMyCommand" value="0x9437" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```  
  
 **如果我.vsct 文件还需要读取较旧版本的 Visual Studio？**  
  
 Visual Studio 早期版本不能识别**IconIsMoniker**命令标志。 在支持它，但继续在较旧版本的 Visual Studio 中使用旧样式映像的版本的 Visual Studio，可以使用映像从映像服务。 若要执行此操作，你将不变 （并因此与 Visual Studio 早期版本兼容），将.vsct 文件，然后从文件创建 CSV （逗号分隔值） 映射的.vsct 文件中定义的 GUID/ID 对\<位图 > 图像的元素名字对象 GUID/ID 对。  
  
 映射 CSV 文件的格式为：  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 与包部署 CSV 文件和其位置由指定**IconMappingFilename**属性**ProvideMenuResource**包属性：  
  
```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 **IconMappingFilename**相对路径隐式某个位于 $PackageFolder$ （如上述示例中），或显式取得 root 在定义的环境变量，如 @"%UserProfile%\ 目录权限的绝对路径dir1\dir2\MyMappingFile.csv"。  
  
## <a name="how-do-i-port-a-project-system"></a>如何端口项目系统？  
 **如何为项目提供 ImageMonikers**  
  
1.  实现**VSHPROPID_SupportsIconMonikers**项目的**IVsHierarchy**，并返回 true。  
  
2.  实现**VSHPROPID_IconMonikerImageList** (如果使用原始项目**VSHPROPID_IconImgList**) 或**VSHPROPID_IconMonikerGuid**， **VSHPROPID_IconMonikerId**， **VSHPROPID_OpenFolderIconMonikerGuid**， **VSHPROPID_OpenFolderIconMonikerId** (如果使用原始项目**VSHPROPID_IconHandle**和**VSHPROPID_OpenFolderIconHandle**)。  
  
3.  更改图标原始 VSHPROPIDs，若要创建的图标的"传统"版本，如果扩展点请求时，这些实现。 **IVsImageService2**提供需获取这些图标的功能  
  
 **额外的要求，对于 VB / C# 项目风格**  
  
 仅实现**VSHPROPID_SupportsIconMonikers**如果检测到你的项目是**外面风格**。 否则为实际的外面风格可能不支持图像名字对象实际上，并且你基风格可能有效地"隐藏"自定义的映像。  
  
 **如何在 CPS 中使用映像名字对象？**  
  
 在 CPS （常见项目系统） 中设置的自定义映像可以进行手动或通过项目系统扩展性 SDK 随附的项模板。  
  
 **使用项目系统可扩展性 SDK**  
  
 按照说明在[提供项目类型/项类型的自定义图标](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md)以自定义 CPS 映像。 CPS 有关的详细信息可以在找到[Visual Studio 项目系统扩展性文档](https://github.com/Microsoft/VSProjectSystem)  
  
 **手动使用 ImageMonikers**  
  
1.  实现并导出**IProjectTreeModifier**项目系统中的接口。  
  
2.  确定哪些**KnownMoniker**或你想要使用的自定义映像名字对象。  
  
3.  在**ApplyModifications**方法，执行以下操作，返回新树中，类似于之前的方法中的某个位置下面的示例：  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  如果要创建新树，则可以设置自定义映像，通过所需的名字对象传入到 NewTree 方法类似于下面的示例：  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
    ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  
  
    return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                 /*filePath*/<value>,  
                                                 /*browseObjectProperties*/<value>,  
                                                 icon,  
                                                 expandedIcon);  
    ```  
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>如何将转换从一个实际图像条到基于标记的图像条？  
 **我需要支持 HIMAGELISTs**  
  
 如果没有为你想要更新使用映像服务，但需要传递图像列表的 Api 将限制您的代码的现有图像条，你仍可以获取映像服务的优势。 若要创建基于标记的图像条，请按照以下步骤来创建从现有的名字对象的清单。  
  
1.  运行**ManifestFromResources**工具，将其传递图像条。 这将生成清单以条带。  
  
    -   建议： 提供的清单以满足其使用情况的非默认名称。  
  
2.  如果仅在使用**KnownMonikers**，然后执行以下操作：  
  
    -   替换\<映像 > 与清单部分\<映像 / >。  
  
    -   删除所有 subimage Id (与任何东西\<imagestrip 名称 > _ # #)。  
  
    -   建议： 重命名的 AssetsGuid 符号和映像条带符号，以满足其使用情况。  
  
    -   将每个**ContainedImage**的 GUID 与 $(ImageCatalogGuid) 替换每个**ContainedImage**的 ID 为 $(\<名字对象 >)，并将外部 ="true"属性添加到每个**ContainedImage**  
  
        -   \<名字对象 > 应替换为**KnownMoniker**操作系统映像映像匹配，但与"KnownMonikers"。 从名称中删除。  
  
    -   添加 < 导入 Manifest="$(ManifestFolder)\\< 相对安装到的目录路径\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest"/\>到顶部\<符号 > 部分。  
  
        -   由安装程序创作清单中定义的部署位置确定的相对路径。  
  
3.  运行**ManifestToCode**工具以生成包装，使现有的代码具有的名字对象，它可用于查询图像条映像服务。  
  
    -   建议： 提供的包装器和命名空间以满足其使用情况的非默认名称。  
  
4.  执行所有操作将添加时，安装程序创作/部署和其他代码更改来使用映像服务和新的文件。  
  
 示例包括内部和外部的映像，以查看它应类似于什么清单：  
  
```xml  
<?xml version="1.0"?>  
<ImageManifest  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  
  <Symbols>  
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest  
         where $(ManifestFolder) is the deployed location of this manifest. -->  
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />  
  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />  
    <ID Name="MyImage_0" Value="100" />  
    <ID Name="MyImage_1" Value="101" />  
    <ID Name="InternalList" Value="1001" />  
    <ID Name="ExternalList" Value="1002" />  
  </Symbols>  
  
  <Images>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">  
      <Source Uri="$(Resources)/MyImage_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">  
      <Source Uri="$(Resources)/MyImage_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  
  <ImageLists>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />  
    </ImageList>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />  
    </ImageList>  
  </ImageLists>  
  
</ImageManifest>  
```  
  
 **我不需要支持 HIMAGELISTs**  
  
1.  确定的一套**KnownMonikers** ，匹配你映像栏中中的映像，或在映像条带中创建你自己的映像的名字对象。  
  
2.  更新用于获取该图像在映像条以改为使用名字对象中所需索引的任何映射。  
  
3.  更新代码以使用图像服务请求通过所更新映射的名字对象。 (这可能意味着更新到**CrispImages**有关托管代码中，或从图像服务请求 HBITMAPs 或 HICONs 和对于本机代码中传递它们。)  
  
## <a name="testing-your-images"></a>测试映像  
 图像库查看器工具可用于测试你图像的清单以确保所有内容正确编写了。 你可以查找中的工具[Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx)。 可以找到有关此工具和其他文档[此处](http://aka.ms/VSImageThemeTools)。  
  
## <a name="additional-resources"></a>其他资源  
  
### <a name="samples"></a>示例  
 已更新多个在 GitHub 上的 Visual Studio 示例来演示如何使用映像服务一部分的各个 Visual Studio 扩展点。  
  
 检查[http://github.com/Microsoft/VSSDK-Extensibility-Samples](http://github.com/Microsoft/VSSDK-Extensibility-Samples)有关最新示例。  
  
### <a name="tooling"></a>工具  
 创建一组映像服务的支持工具以帮助创建/更新适用于映像服务的用户界面。 有关每个工具的详细信息，请检查工具所附带的文档。 这些工具是的一部分包括[Visual Studio 2015 SDK。](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 从资源工具清单图像资源 （PNG 或 XAML） 的列表，并生成图像清单文件中使用这些映像的映像服务。  
  
 **ManifestToCode**  
  
 代码工具清单使用图像清单文件，并生成引用代码 （c + +、 C# 或 VB） 或.vsct 文件中的清单值的包装器文件。  
  
 **ImageLibraryViewer**  
  
 图像库查看器工具可以加载图像的清单，并允许用户用来处理它们与 Visual Studio 将以确保正确编写了清单的方式相同。 用户可以更改背景、 大小、 DPI 设置、 高对比度和其他设置。 它还显示加载信息用来在清单中查找错误，并在清单中显示每个图像的源信息。  
  
## <a name="faq"></a>FAQ  
  
-   是否有任何必须包括在加载时的依赖关系\<引用 Include="Microsoft.VisualStudio.*。Interop.14.0.DesignTime"/ >？  
  
    -   设置 EmbedInteropTypes ="true"上的所有互操作的 Dll。  
  
-   如何部署扩展名为我的映像清单？  
  
    -   将.imagemanifest 文件添加到你的项目。  
  
    -   设置为 True 的"将包括在 VSIX"。  
  
-   我正在更新我 CPS 项目系统。 发生了什么情况**ImageName**和**StockIconService**？  
  
    -   o 这些已删除时 CPS 已更新为使用名字对象。 不再需要调用**StockIconService**，只需传递所需**KnownMoniker**对方法或属性使用**ToProjectSystemType()**中的扩展方法CPS 实用程序。 你可以找到从映射**ImageName**到**KnownMonikers**下面：  
  
        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  
  
    -   我正在更新我的完成列表提供程序。 什么**KnownMonikers**与旧匹配**StandardGlyphGroup**和**StandardGlyph**值？  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
        |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
        |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
        |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
        |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
        |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
        |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
        |GlyphGroupType|GlyphItemPublic|TypePublic|  
        |GlyphGroupType|GlyphItemInternal|TypeInternal|  
        |GlyphGroupType|GlyphItemFriend|TypeInternal|  
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||ClassFile|  
        |GlyphAssembly||参考|  
        |GlyphLibrary||库|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||对话框|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||GoToNext|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||代码段|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||递归|  
        |GlyphXmlItem||标记|  
        |GlyphJSharpProject||DocumentCollection|  
        |GlyphJSharpDocument||Document|  
        |GlyphForwardType||GoToNext|  
        |GlyphCallersGraph||CallTo|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||CallTo|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||xmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|