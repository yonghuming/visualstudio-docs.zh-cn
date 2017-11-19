---
title: "寻址 DPI 问题 2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e944c8a998a3e8bba46d5018faf1b9103a91240
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="addressing-dpi-issues"></a>寻址 DPI 问题
越来越多的设备将随"高分辨率"屏幕。 这些屏幕通常具有超过 200 个每英寸像素数 (ppi)。 使用这些计算机上的应用程序将需要要向上扩展以满足的需求查看设备的正常查看距离处的内容的内容。 从 2014 年开始高密度显示的主要目标是移动计算设备 （平板电脑、 壳式便携式计算机和手机）。  
  
 Windows 8.1 和更高版本包含几个功能，可使这些计算机能够与显示和环境，其中该机附加到这两种高密度和标准密度显示在同一时间工作。  
  
-   Windows 可缩放内容以使用"使文本和其他项放大或缩小"的设备为允许你设置 （可用自 Windows XP 起）。  
  
-   Windows 8.1 和更高版本将自动缩放内容对于大多数应用程序保持一致时显示的不同像素密度之间移动。 当主显示器是高密度 （200%缩放） 辅助显示为标准密度 （100%)，Windows 将自动减少了应用程序窗口的内容辅助显示屏上 (1 个像素显示呈现的每个 4 个像素应用程序）。  
  
-   Windows 将默认为在缩放像素密度并查看显示 (Windows 7 和更高版本，OEM 可配置) 的距离的权利。  
  
-   Windows 可以自动缩放内容向上到 250%超过 280 ppi （截至 Windows 8.1 S14) 的新设备上。  
  
 Windows 拥有一种处理 UI 向上扩展的方式，以利用的增加的像素数。 应用程序来选择加入到此系统通过将其自身声明为"system 识别 DPI。 请执行此操作的应用程序是向上扩展系统。 这可以导致整个应用程序所在统一像素拉伸"模糊"用户体验。 例如:   
  
 ![DPI 问题模糊](../extensibility/media/dpi-issues-fuzzy.png "DPI 问题模糊")  
  
 Visual Studio 选择正在 DPI 缩放感知型，并因此不"虚拟化的。"  
  
 Windows （和 Visual Studio） 利用多种 UI 技术，其具有不同的缩放比例系数系统设置的处理方式。 例如:   
  
-   WPF 测量控件的独立于设备的方式 （单位，不是以像素）。 注册当前 DPI 自动缩放 WPF UI。  
  
-   无论 UI 框架的所有文本大小以磅为单位，表示，并因此都将被作为独立于 DPI 的系统。 Win32、 WinForms 和 WPF 中的文本已向上扩展正确绘制到显示设备时。  
  
-   Win32/WinForms 对话框和窗口具有用于启用调整大小适应 text-例如，通过网格、 流和表布局面板的布局方式。 这些筛选器可避免不调整字体大小会增加时的硬编码像素位置。  
  
-   系统提供的图标或根据系统度量值 （例如，SM_CXICON 和 SM_CXSMICON） 的资源已向上扩展。  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>较旧的 Win32 GDI (GDI +） 和基于 WinForms 的 UI  
 已高 DPI 感知 WPF 时，很多我们基于 Win32/GDI 的代码未最初写入用记住 DPI 感知。 Windows 提供的 DPI 缩放 Api。 Win32 问题的修补程序应使用这些一致地跨产品。 Visual Studio 提供了一个帮助程序类库，以避免复制功能，并确保跨产品一致性。  
  
## <a name="high-resolution-images"></a>高分辨率的图像  
 本节是主要用于开发人员在扩展 Visual Studio 2013。 对于 Visual Studio 2015 中，使用内置于 Visual Studio 映像服务。 您还可能会发现你需要支持/目标多个版本的 Visual Studio，并且因此使用 2015年中的映像服务不是选项由于不存在以前版本中。 本部分也是为你然后。  
  
## <a name="scaling-up-images-that-are-too-small"></a>按比例增加太小的图像  
 可以向上扩展"并 GDI 和使用某些常见的方法的 WPF 呈现图像太小。 托管的 DPI 帮助器类可供内部和外部 Visual Studio 集成商到缩放图标、 位图、 imagestrips 和 imagelists 的地址。 基于 Win32 的本机 C / C + + 帮助程序是可用于缩放任务栏、 HBITMAP、 HIMAGELIST 和 VsUI::GdiplusImage。 缩放的位图通常仅需要一个行更改后包括对的帮助程序库的引用。 例如:   
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 缩放 imagelist 取决于 imagelist 负载时，已完成还是追加在运行时。 如果在加载时完成，调用 LogicalToDeviceUnits() imagelist 像位图。 在该代码需要编写 imagelist 之前加载各个位图，请确保要缩放的 imagelist 图像大小：  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 在本机代码中，按如下所述创建 imagelist 时，可以扩展维度：  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 库中的函数允许指定的大小调整的算法。 当缩放图像放入 imagelists，请确保指定对透明度、 使用的背景色，或使用 NearestNeighbor 缩放 （这将导致在 125%和 150%扭曲）。  
  
 请查阅<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>MSDN 上的文档。  
  
 下表显示图像缩放以相应 DPI 的方式的示例缩放比例系数。 绿色中的映像表示截至 Visual Studio 2013 （100%-200 %dpi 缩放） 我们最佳做法：  
  
 ![DPI 问题缩放](../extensibility/media/dpi-issues-scaling.png "DPI 问题缩放")  
  
## <a name="layout-issues"></a>布局问题  
 主要由保持点，在 UI 中扩展和相对于另一个，而非通过使用绝对位置 （具体而言，以像素为单位），则可以避免常见的布局问题。 例如:   
  
-   布局/文本位置需要调整到的扩展型映像的帐户。  
  
-   在网格中的列需要的调整扩展型文本的宽度。  
  
-   硬编码的大小或元素之间空白区域还需要向上扩展。 仅基于文本维度的大小是通常合适的因为字体自动缩放。  
  
 中提供了帮助器函数<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>类，以允许扩展 X 和 Y 轴上：  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (函数允许按比例 X / Y 轴)  
  
-   int 空间 = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   int 高度 = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 有 LogicalToDeviceUnits 重载，以允许扩展对象，例如 Rect、 点和大小。  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>使用 DPIHelper 库/类到缩放图像和布局  
 Visual Studio DPI 帮助程序库可在本机和托管的窗体中，并可由其他应用程序在 Visual Studio shell 之外。  
  
 若要使用库，请转到[Visual Studio VSSDK 扩展性示例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)和克隆高 DPI_Images_Icons 示例  
  
 在源代码文件中包括 VsUIDpiHelper.h 和调用 VsUI::DpiHelper 类的静态函数：  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  不要在模块级别或类级别的静态变量中使用的帮助器函数。 库还用于线程同步使用的静态对象，并可能会遇到顺序初始化问题。 将这些静态对象转换为非静态成员变量，或者将它们包装到的函数 （以便在首次访问获取构造它们）。  
  
 若要从将在 Visual Studio 环境内运行的托管代码访问的 DPI 帮助器函数：  
  
-   使用项目必须引用 Shell MPF 的最新版本。 例如:   
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   确保项目具有对引用**System.Windows.Forms**， **PresentationCore**，和**PresentationUI**。  
  
-   在代码中，使用**Microsoft.VisualStudio.PlatformUI** DpiHelper 类的命名空间和调用静态函数。 对于支持的类型 （点、 大小、 矩形和等等），没有提供返回新的扩展函数扩展对象。 例如:   
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>在可缩放的用户界面中的 WPF 映像画质模糊不清处理  
 在 WPF 中，位图自动进行调整 WPF 通过为使用高质量两次立方算法 （默认值），这非常适用于图片或大屏幕快照，但不适合于菜单项图标，因为它引入感知画质模糊不清的当前 DPI 缩放级别.  
  
 建议：  
  
-   徽标图像和横幅图片，默认值为<xref:System.Windows.Media.BitmapScalingMode>无法使用大小调整模式。  
  
-   菜单项和插图图像，<xref:System.Windows.Media.BitmapScalingMode>时它不会导致其他扭曲项目以消除颜色容差 （在 200%和 300%），应使用。  
  
-   为大缩放级别不的 100%（例如，250%或 350%） 的倍数，缩放与双立方插图图像会导致模糊、 冲蚀用户界面。 通过第一个缩放为 100%（例如，200%或 300%） 的最大倍数 NearestNeighbor 的映像并从那里的双立方类扩展获取更好的结果。 看一看特殊案例： 对于大型 dpi，分辨率 prescaling WPF 映像级别的详细信息。  
  
 Microsoft.VisualStudio.PlatformUI 命名空间中的 DpiHelper 类提供成员<xref:System.Windows.Media.BitmapScalingMode>被用于绑定。 它还允许 Visual Studio shell 来控制统一，具体取决于 DPI 缩放因子缩放模式下跨产品的位图。  
  
 若要在 XAML 中使用它，添加：  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell 已在顶级窗口和对话框上设置此属性。 在 Visual Studio 中运行的基于 WPF 的 UI 已继承它。 如果设置不会传播到你的特定部分 UI 中，可以在 XAML/WPF UI 的根元素上设置。 可能出现此问题的位置包括弹出窗口，Win32 父级的元素和设计器外运行的 windows 进程，如 Blend。  
  
 某些 UI 可以独立于系统集 DPI 缩放级别，例如 Visual Studio 文本编辑器和基于 WPF 的设计器 （WPF 桌面版和 Windows 应用商店） 扩展。 在这些情况下，不应使用 DpiHelper.BitmapScalingMode。 若要解决此问题，在编辑器中，IDE 团队创建自定义属性，标题为 RenderOptions.BitmapScalingMode。 将该属性值设置为 HighQuality 或 NearestNeighbor 中，具体取决于系统和你的 UI 的组合的缩放级别。  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>特殊情况： prescaling 大 DPI 级别的 WPF 图像  
 对于不是 100%（例如，250%、 350%等） 的倍数的非常大的缩放级别，缩放双三次在中使用结果模糊、 冲蚀 UI 的插图图像。 这些映像清晰文本旁的印象几乎是类似的光学视觉效果。 显示图像以更接近人眼和传出相对于文本的焦点。 可以通过第一个缩放为 100%（例如，200%或 300%） 的最大倍数 NearestNeighbor 的映像和扩展到剩余部分 （其他 50%) 的双立方改进缩放结果在此项目的大小。  
  
 以下是一种差异在结果中，其中的第一个图像进行缩放后使用 100%-> 改进双缩放的算法 200%-> 250%和第二个只需使用双立方 100%-> 250%。  
  
 ![DPI 问题 Double 缩放示例](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 问题 Double 缩放示例")  
  
 若要启用 UI，以使用此双缩放，XAML 标记来显示每个图像元素将需要修改。 下面的示例演示如何使用使用 DpiHelper 库和 Shell.12/14 的 Visual Studio 中的 WPF 中的双缩放。  
  
 步骤 1: Prescale 200%到 300%，依此类推使用 NearestNeighbor。  
  
 Prescale 使用任一转换器应用在绑定上，或使用 XAML 标记扩展的映像。 例如:   
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 如果还需要具有主题映像 （大多数情况下，如果不是全部，应），标记可以使用不同的转换器首先执行的图像，然后预缩放的主题。 标记可以使用两个<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter>或<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>，取决于所需的转换输出。  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 步骤 2： 确保最终大小是正确的当前 DPI。  
  
 因为对于使用在 ui 元素上设置 BitmapScalingMode 属性当前 dpi，分辨率，WPF 将缩放 UI，应使用 prescaled 的映像作为其源将查找两个或三个时间比它大图像控件。 以下是几种方式为了应对这种效果：  
  
-   如果你知道的维度的以 100%的原始映像，你可以指定图像控件的确切大小。 这些大小将反映应用之前缩放 UI 的大小。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   如果不知道原始图像的大小，可以使用 LayoutTransform 以缩小最终映像对象。 例如:   
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>启用到 WebOC 的 HDPI 支持  
 默认情况下，WebOC 控件 （如 WPF 中或 IWebBrowser2 接口中的 WebBrowser 控件） 不启用 HDPI 检测和支持。 结果将是具有高分辨率的显示器太小的显示内容的嵌入的控件。 以下介绍如何启用特定 web WebOC 实例中的高 DPI 支持。  
  
 实现 IDocHostUIHandler 接口 (请参阅 MSDN 文章[IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx)接口):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 （可选） 实现 ICustomDoc 接口 (请参阅 MSDN 文章[ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx)接口):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 将实现 IDocHostUIHandler 与 WebOC 的文档的类相关联。 如果实现上述 ICustomDoc 接口，然后立即 WebOC 的文档属性才有效，将其转换为 ICustomDoc 和调用传递的类的实现 IDocHostUIHandler SetUIHandler 方法。  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 如果你未实现 ICustomDoc 接口，然后就会立即 WebOC 的文档属性才有效，你将需要将其转换为 IOleObject，然后调用 SetClientSite 方法，传递的类中实现 IDocHostUIHandler。 设置传递到 GetHostInfo 方法调用 DOCHOSTUIINFO DOCHOSTUIFLAG_DPI_AWARE 标志：  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 这应是所有你需要先获得 WebOC 控件，以支持 HPDI。  
  
## <a name="tips"></a>提示  
  
1.  如果 WebOC 控件上的文档属性发生更改，你可能需要将文档与 IDocHostUIHandler 类重新关联。  
  
2.  如果上述不起作用，则不选取更改为 DPI 标志 WebOC 的已知的问题。 修复这的最可靠方法是切换 WebOC，使用两个不同的缩放百分比值的含义两个调用光学缩放。 此外，如果不需要此解决方法，它可能有必要执行上的每个导航调用。  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```