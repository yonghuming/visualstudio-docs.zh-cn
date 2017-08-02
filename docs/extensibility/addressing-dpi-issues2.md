---
title: "寻址 DPI 问题&amp;2; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 解决 DPI 问题
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

越来越多的设备都具有"高分辨率"屏幕。 这些屏幕通常具有超过 200 个像素 \/ 英寸 \(ppi\)。 使用这些计算机上的应用程序将要求进行内容来扩展以满足需要查看该设备正常查看距离处的内容。 从 2014年开始，高密度显示的主要目标是移动计算设备 （平板电脑、 蛤便携式计算机和手机）。  
  
 Windows 8.1 及更高版本包含多种功能，可使这些计算机能够与显示和环境的计算机连接到这两种高密度、 何地标准密度显示在同一时间起作用。  
  
-   Windows 可以允许您缩放内容以使用"使文本和其他项目放大或缩小"的设备设置 （Windows XP 以来可用）。  
  
-   Windows 8.1 及更高版本将自动缩放内容对于大多数应用程序，使其显示的不同像素密度之间移动时保持一致。 当主显示器高密度 （200%缩放），辅助显示是标准密度 （100%\) 时，Windows 将自动减少了应用程序窗口的内容上辅助显示 （为每个应用程序呈现的 4 个像素显示 1 个像素）。  
  
-   Windows 将默认为在缩放像素密度并查看显示 \(Windows 7 及更高版本，OEM 可配置\) 的距离的权利。  
  
-   Windows 可以自动缩放设置为 250%内容在超过 280 ppi （截止到 Windows 8.1 S14\) 的新设备上。  
  
 Windows 包含一种处理向上 UI 扩展以利用增加的像素计数。 应用程序来选择加入到此系统通过将自身声明"system 感知 DPI。 由系统，向上扩展应用程序，请执行此操作。 这可以导致整个应用程序是统一像素拉伸的"模糊"用户体验。 例如:  
  
 ![DPI 问题 模糊](../extensibility/media/dpi-issues-fuzzy.png "DPI Issues Fuzzy")  
  
 Visual Studio ︰ 选择加入正在 DPI 缩放识别，并因此未"虚拟化。"  
  
 Windows （和 Visual Studio） 利用了几种 UI 技术，具有不同的缩放比例系数系统设置的处理方式。 例如:  
  
-   WPF 测量控件以独立于设备的方式 （单位，不是以像素）。 为当前的 DPI 自动缩放 WPF UI。  
  
-   无论 UI 框架的所有文本大小以磅为单位，表示，并因此会根据 DPI 独立系统处理。 Win32、 WinForms 和 WPF 中的文本已扩大规模正确绘制到显示设备时。  
  
-   Win32\/WinForms 对话框和窗口具有用于启用可调整大小适应文本 – 例如，通过网格、 流和表布局面板的布局。 这些筛选器可避免在字体大小将会增加时不作缩放的硬编码像素位置。  
  
-   系统提供的图标或基于系统度量值 （例如，SM\_CXICON 和 SM\_CXSMICON） 资源已向上扩展。  
  
## 较旧的 Win32 （GDI、 GDI \+） 和基于 WinForms 的用户界面  
 WPF 已高 DPI 感知，而我们基于 Win32\/GDI 的代码大部分未最初使用编写记住 DPI 识别。 Windows 提供的 DPI 缩放 Api。 Win32 问题的修补程序应使用这些一致地跨产品。 Visual Studio 提供了一个帮助器类库，以避免复制功能和确保跨产品的一致性。  
  
## 高分辨率的图像  
 本部分主要是为了开发人员在扩展 Visual Studio 2013。 对于 Visual Studio 2015 中，使用内置于 Visual Studio 图像服务。 您可能会发现您需要支持\/目标许多版本的 Visual Studio，并因此 2015年中使用图像服务不可避免由于不存在以前版本中。 本部分也是为您然后。  
  
## 太小的图像向上扩展  
 可以""向上扩展和 GDI 和 WPF 中使用一些公共方法呈现太小的图像。 托管的 DPI 帮助器类可供内部和外部 Visual Studio 集成商到缩放图标、 位图、 imagestrips 和 imagelists 的地址。 基于 Win32 的本机 C \/ C \+ \+ 帮助程序是可用于缩放 HICON、 HBITMAP、 HIMAGELIST 和 VsUI::GdiplusImage。 通常一个位图的缩放比例只需要一行更改包括对帮助程序库的引用后。 例如:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 缩放 imagelist 取决于 imagelist 在加载时，已完成还是在运行时附加。 如果在加载时完成，调用 LogicalToDeviceUnits\(\) imagelist 就像一个位图。 当代码需要在撰写 imagelist 之前加载各个位图时，请务必要缩放的 imagelist 图像大小 ︰  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 在本机代码中，如下所示创建 imagelist 时，可以扩展维度 ︰  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 库中的函数允许指定的大小调整的算法。 当缩放图像以放置在 imagelists，请确保指定的透明度，使用的背景色，或使用 NearestNeighbor 缩放 （这将导致在 125%和 150%扭曲）。  
  
 请查阅 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN 上的文档。  
  
 下表显示示例应如何以相应的 DPI 缩放图像的缩放比例系数。 以绿色图像表示从 Visual Studio 2013 （100%的 200 %dpi 缩放） 起我们最佳实践 ︰  
  
 ![DPI 问题 缩放](~/docs/extensibility/media/dpi-issues-scaling.png "DPI Issues Scaling")  
  
## 布局问题  
 主要通过扩展用户界面中，并相对于另一个保留点而不是使用绝对位置 （具体而言，以像素为单位），可以避免常见的布局问题。 例如:  
  
-   布局\/文本位置需要进行调整到对于扩展型映像的帐户。  
  
-   在网格中的列必须有调整扩展型文本的宽度。  
  
-   硬编码的大小或元素之间空白区域还需要向上扩展。 仅基于文本尺寸的大小是通常没问题，，因为字体自动缩放。  
  
 中提供了帮助器函数 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> 类，以允许在 X 和 Y 轴上缩放 ︰  
  
-   LogicalToDeviceUnitsX\/LogicalToDeviceUnitsY \(函数允许扩展在 X \/ Y 轴\)  
  
-   int 空间 \= DpiHelper.LogicalToDeviceUnitsX \(10\);  
  
-   int 高度 \= VsUI::DpiHelper::LogicalToDeviceUnitsY\(5\);  
  
 有 LogicalToDeviceUnits 重载，以允许缩放对象，如 Rect、 点和大小。  
  
## 使用 DPIHelper 库\/类对缩放图像和布局  
 Visual Studio DPI 帮助程序库也可在本机和托管窗体可由其他应用程序之外的 Visual Studio shell。  
  
 若要使用的库，请转到 [Visual Studio VSSDK 扩展性示例](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 和克隆高 DPI\_Images\_Icons 示例  
  
 源代码文件中包括 VsUIDpiHelper.h 并调用 VsUI::DpiHelper 类的静态函数 ︰  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  不要在模块级别或类级别的静态变量中使用的帮助器函数。 库还将用于线程同步的静态变量，并且可能会遇到顺序初始化问题。 将这些静态对象转换为非静态成员变量，或者将它们包装到函数 （因此它们获取构造，在首次访问）。  
  
 若要从将在 Visual Studio 环境中运行的托管代码访问 DPI 帮助器函数 ︰  
  
-   在使用项目必须引用外壳 MPF 最新版本。 例如:  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   确保项目所引用的 **System.Windows.Forms**, ，**PresentationCore**, ，和 **PresentationUI**。  
  
-   在代码中，使用 **Microsoft.VisualStudio.PlatformUI** DpiHelper 类的命名空间和调用静态函数。 为支持的类型 （点、 大小、 矩形和等等），有一些提供返回新的扩展函数扩展对象。 例如:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## WPF 图像颜色容差 zoomable 用户界面中处理  
 在 WPF 中，位图是自动调整大小由 WPF 使用高质量两次立方算法 （默认值），这非常适合图片或大型屏幕快照，但不适合于菜单项图标，因为它引入了让人察觉颜色容差的当前 DPI 缩放级别。  
  
 建议 ︰  
  
-   徽标图像和横幅图片，默认值为 <xref:System.Windows.Media.BitmapScalingMode> 可能使用调整大小模式。  
  
-   为菜单项和插图图像 <xref:System.Windows.Media.BitmapScalingMode> 时它不会导致其他失真项目以消除颜色容差 （在 200%和 300%），应使用。  
  
-   •	对于大缩放级别不为 100%（例如，250%或 350%） 的倍数，缩放与双立方插图图像会导致模糊、 冲蚀用户界面。 通过第一个扩展到 100%（例如，200%或 300%） 的最大倍数 NearestNeighbor 映像，然后从那里双三次使用进行缩放获取更好的结果。 看一看特殊案例 ︰ 对大型 DPI prescaling WPF 图像的详细信息级别。  
  
 Microsoft.VisualStudio.PlatformUI 命名空间中的 DpiHelper 类提供了成员 <xref:System.Windows.Media.BitmapScalingMode> 要用于进行绑定。 它将允许 Visual Studio shell 来控制均匀，具体取决于 DPI 比例因子缩放模式下跨产品的位图。  
  
 若要使用它在 XAML 中，添加 ︰  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell 已经在顶级窗口和对话框上设置此属性。 在 Visual Studio 中运行的基于 WPF 的 UI 已经将继承该权限。 如果该设置不会传播到您的特定部分 UI，它可以设置 XAML\/WPF UI 的根元素上。 其中发生这种情况的地方包括弹出窗口，在 Win32 父级的元素上和进程外运行的设计器窗口，如混合。  
  
 一些 UI 可以独立于系统组的 DPI 缩放级别，例如 Visual Studio 文本编辑器和基于 WPF 的设计器 （WPF 桌面和 Windows 应用商店） 进行缩放。 在这些情况下，不应使用 DpiHelper.BitmapScalingMode。 若要解决此问题，在编辑器中，所创建的自定义属性的 IDE 团队的标题为 RenderOptions.BitmapScalingMode。 将该属性值设置为 HighQuality 或 NearestNeighbor 中，具体取决于系统和用户界面的组合的缩放级别。  
  
## 特殊情况 ︰ prescaling 大 DPI 级别的 WPF 图像  
 对于不是 100%（例如，250%、 350%等） 的倍数的非常大的缩放级别，缩放与模糊、 冲蚀 UI 中的两次立方结果的插图图像。 这些图像清晰文本旁的印象，几乎就像的光学视觉效果。 显示图像，用于更接近眼看并且失去焦点相对于文本。 在这种放大大小缩放的结果可以提高通过第一个扩展到 100%（例如，200%或 300%） 的最大的多个与 NearestNeighbor 图像，然后使用两次立方给 （其他的 50%\) 的其余部分进行缩放。  
  
 以下是在结果中，差异的示例将第一个图像进行缩放，与改进双缩放的算法 100%\-\> 200%\-\> 250%和第二个只需使用双立方 100%\-\> 250%。  
  
 ![DPI Issues Double Scaling Example](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Issues Double Scaling Example")  
  
 若要启用用户界面以可使用此双缩放、 XAML 标记来显示每个 Image 元素将需要进行修改。 下面的示例演示如何在 Visual Studio 中使用 DpiHelper 库和 Shell.12\/14 中使用双缩放在 WPF 中。  
  
 步骤 1: Prescale 300%到 200%、 图像等使用 NearestNeighbor。  
  
 Prescale 使用任一转换器应用在绑定上，或与 XAML 标记扩展的映像。 例如:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 如果还需要有主题图像 （大多数情况下，如果不是全部，应该），标记可以使用不同的转换器，第一次执行的图像，然后预缩放的主题。 标记可以使用两个 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> 或 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, ，取决于所需的转换输出。  
  
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
  
 步骤 2 ︰ 确保最终大小是正确的当前 DPI。  
  
 由于 WPF 将当前使用 BitmapScalingMode 属性在 UIElement 上设置的 dpi 缩放用户界面，应使用 prescaled 的图像作为其源将查找两个或三个时间比它大图像控件。 以下是几种方法，以应对这种效果 ︰  
  
-   如果您知道在 100%原始图像的维度，您可以指定图像控件的确切大小。 这些大小将反映应用之前扩展用户界面的大小。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   如果不知道原始图像的大小，可以使用 LayoutTransform 缩减最终的 Image 对象。 例如:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## 启用到 WebOC HDPI 支持  
 默认情况下，HDPI 检测和支持，不要启用 WebOC 控件 （如 WPF 中或 IWebBrowser2 接口中的 web 浏览器控件）。 结果将是一个嵌入的控件分别具有太小，高分辨率显示器的显示内容。 以下介绍如何启用特定的 web WebOC 实例中的高 DPI 支持。  
  
 实现 IDocHostUIHandler 接口 \(有关，请参阅 MSDN 文章 [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) 接口\):  
  
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
  
 （可选） 实现 ICustomDoc 接口 \(有关，请参阅 MSDN 文章 [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) 接口\):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 将实现 IDocHostUIHandler 与 WebOC 的文档的类相关联。 如果实现上述的 ICustomDoc 接口，然后只要 WebOC 的文档属性是有效的将其转换为 ICustomDoc 并调用 SetUIHandler 方法，并传递实现 IDocHostUIHandler 的类。  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 如果未实现 ICustomDoc 接口，然后只要 WebOC 的文档属性是有效的您需要将其转换为 IOleObject，然后调用 SetClientSite 方法，传入实现 IDocHostUIHandler 的类。 设置传递给 GetHostInfo 方法调用 DOCHOSTUIINFO DOCHOSTUIFLAG\_DPI\_AWARE 标志 ︰  
  
```c#  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 这应该是所有您需要先获取 WebOC 控件支持 HPDI。  
  
## 提示  
  
1.  如果 WebOC 控件上的文档属性发生更改，您可能需要将文档与 IDocHostUIHandler 类重新关联。  
  
2.  如果上述操作失败，则不选取更改为 DPI 标志 WebOC 的已知的问题。 修复这的最可靠的方法是切换 WebOC 含义两次调用两个值不同的缩放百分比的光学缩放。 此外，如果需要此解决方法，它可能需要在每次导航调用上执行。  
  
    ```c#  
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