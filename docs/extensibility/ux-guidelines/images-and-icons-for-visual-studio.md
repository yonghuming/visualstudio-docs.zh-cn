---
title: "映像和 Visual Studio 的图标 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 映像和 Visual Studio 的图标
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="a-namebkmkimageuseinvisualstudioa-image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Visual Studio 中的图像使用  
 在创建图片之前, 请考虑进行中的 1000 多种图像使用 [Visual Studio 图像库](http://www.microsoft.com/en-my/download/details.aspx?id=35825)。  
  
### <a name="types-of-images"></a>类型的图像  
  
-   **图标**。 出现在命令、 层次结构、 模板和等等的小图像。 在 Visual Studio 中使用的默认图标大小为 16 x 16 PNG。 自动生成的映像服务的图标生成 HDPI 支持 XAML 格式。  
  
     **注意︰** 菜单系统中使用的映像，而不应创建的每个命令的图标。 请查阅 [菜单和命令对 Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) 以查看您的命令是否应获得一个图标。  
  
-   **缩略图。** 对话框中，如新建项目对话框中的预览区域中使用的图像。  
  
-   **对话框的图像。** 在对话框或向导，作为描述性图形或消息指示器中显示的图像。 很少并且仅在必要说明困难概念或获得用户的注意力 （警报，警告） 时使用。  
  
-   **带动画的图像。** 在进度指示器、 状态栏和操作对话中使用。  
  
-   **游标。** 用于指示是否使用的鼠标的对象可能会断开，并等的位置，才允许的操作。  
  
##  <a name="a-namebkmkicondesigna-icon-design"></a><a name="BKMK_IconDesign"></a> 图标设计  
  
### <a name="overview"></a>概述  
 Visual Studio 将使用现代样式图标，它具有全新的 geometry 和正/负 （浅/深） 的 50/50 余额，使用直接、 易于理解的形式。 重要图标设计点周围的清晰度、 简化和上下文的中心。  
  
-   **为了清楚起见︰** 专注于为其含义和独特性与提供了一个图标的核心隐喻。  
  
-   **简化︰** 减少图标到其核心意义 – 可以主题通过只是必需的元素和无修饰。  
  
-   **上下文︰** 概念在开发期间，这至关重要，在决定哪些元素构成的图标核心比喻时，请考虑一个图标角色的所有方面。  
  
 带图标，有大量的设计要点，以免︰  
  
-   不要使用在适当的时候表示除 UI 元素的图标。 UI 元素既不常见，很明显，也不唯一时，请选择更抽象的或符号的方式。  
  
-   过度使用常用的元素不喜欢的文档、 文件夹、 箭头和放大镜。 使用此类元素只在必需的图标的含义时。 例如，朝右放大镜应指示仅搜索、 浏览和查找。  
  
-   尽管某些旧图标元素保持透视图的用途，不创建新的图标与角度来看除非该元素缺少清楚起见，如果没有该软件。  
  
-   不要将太多的信息转换为图标。 一个简单的图像，可以轻松地识别或了解了更多有用的过于复杂的映像相比，可识别符号原样。 图标不能告诉整篇文章。  
  
### <a name="icon-creation"></a>图标创建  
  
#### <a name="concept-development"></a>概念开发  
 Visual Studio 在其用户界面内有各种图标类型。 在开发过程中，请仔细考虑图标类型。 不要使用不清晰或非同寻常 UI 对象执行所选图标的元素。 选择符号在这些情况下，如带智能标记图标。 请注意在左侧的抽象标记的含义变得更加明显比右侧的含糊不清的、 基于 UI 的版本︰  
  
|||  
|-|-|  
|**正确使用的符号的图像**|**不正确地使用的符号的图像**|  
|![正确的“智能标记”图标](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![不正确的“智能标记”图标](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|  
  
 有在其中标准的、 易于识别的用户界面元素适用于图标的实例。 添加窗口是一个这样的例子︰  
  
|||  
|-|-|  
|**在图标中正确的 UI 元素**|**错误图标的 UI 元素**|  
|![正确的“添加窗口”图标](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![不正确的“添加窗口”图标](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|  
  
 不使用文档作为基元素，除非它是至关重要的图标的含义。 不使用文档 （见下文） 含义上添加文档元素会丢失，而使用更新的文档元素不需要传达的含义。  
  
|||  
|-|-|  
|**正确地使用文档图标**|**不正确地使用文档图标**|  
|![正确的“文档”图标](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![不正确的“文档”图标](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|  
  
 应由最适合对所显示的内容，如与显示所有文件示例的图标表示"显示"的概念。 镜头比喻可能用于指示这一概念的"视图"，如有必要，如资源视图的示例。  
  
|||  
|-|-|  
|**"显示"**|**"视图"**|  
|![“显示”图标](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![“查看”图标](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|  
  
 朝右放大玻璃图标应表示仅搜索、 查找和浏览。 朝左变体与加号或减号应表示唯一放大/缩小。  
  
|||  
|-|-|  
|**"搜索"**|**"缩放"**|  
|![“搜索”图标](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![“缩放”图标](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|  
  
 在树视图中，不要使用文件夹图标和修饰符。 如果可用，请使用仅修饰符。  
  
|||  
|-|-|  
|**正确的树视图图标**|**不正确的树视图图标**|  
|![正确的树视图图标和 #40; 1 和 #41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![正确的树视图图标和 #40; 2 和 #41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![不正确的树视图图标和 #40; 1 和 #41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![不正确的树视图图标和 #40; 2 和 #41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>样式的详细信息  
  
#### <a name="layout"></a>布局  
 堆栈元素的标准 16x16 图标所示︰  
  
 ![16x16 图标的布局堆栈](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")  
  
 **16x16 图标的布局堆栈**  
  
 状态通知元素是更好地用作独立图标。 有以下的上下文中，但是，在其中通知应会堆叠在基元素，如与任务完成图标︰  
  
 ![Visual Studio 中的独立通知](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")  
  
 **独立通知图标**  
  
 ![“任务完成”图标](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")  
  
 **任务完成图标**  
  
 项目图标通常是包含多个大小的.ico 文件。 大多数 16x16 图标包含相同的元素。 32 x 32 版本具有更多详细信息，包括时适用的项目类型。  
  
 ![Visual Studio 中的“项目”图标](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")  
  
 **VB Windows 控件库项目图标，16 x 16 和 32 x 32**  
  
 中心其像素框架中的图标。 如果不可能，调整到文件的顶部和/或帧的右侧的图标。  
  
 ![图标在像素框架中居中](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")  
  
 **图标在像素框架中居中**  
  
 ![图标与像素框架的右上方对齐](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")  
  
 **图标的顶部对齐的框架的权限**  
  
 ![图标居中并与像素框架的顶部对齐](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")  
  
 **图标居中并与框架的顶部对齐**  
  
 若要实现理想的对齐方式和平衡，避免不阻止操作的标志符号的图标的基本元素。 左上角基元素的顶部附近的标志符号的位置。 在添加了另一个元素时，请考虑的对齐方式和图标的平衡。  
  
|||  
|-|-|  
|**正确的对齐方式和平衡**|**未正确对齐和平衡**|  
|![正确的图标平衡和对齐方式](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![不正确的图标平衡和对齐方式](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|  
  
 确保共享元素，集中使用的图标的大小相同。 请注意，在不正确配对，圆形和箭头过大，不匹配。  
  
|||  
|-|-|  
|**正确的大小奇偶校验**|**大小不正确奇偶校验**|  
|![正确的图标的大小和奇偶校验](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![不正确的图标的大小和奇偶校验](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|  
  
 使用一致的行和可视化的权重。 评估如何您构建的图标为其他图标使用比较通过并行比较。 永远不会使用整个 16 x 16 框架，则使用 15 x 15 或更小。 负正 （深浅） 比应为 50/50。  
  
|||  
|-|-|  
|**正确的负正比**|**不正确的负正比率**|  
|![更正视觉对象粗细的图标和 #40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![更正视觉对象粗细的图标和 #40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![更正视觉对象粗细的图标和 #40; 3 &#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![不正确的图标视觉重量](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|  
  
 使用简单、 可比较形状和相互补充角度而不牺牲元素完整性生成所选的元素。 如果可能，请使用 45 度或 90 度角。  
  
 ![正确的图标角度](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>透视  
 保持图标清楚明了。 透视和光源仅在必要时使用。 虽然应避免使用图标元素上的角度来看，但某些元素是没有它无法识别。 在这种情况下，风格化的角度来看进行通信元素的清晰度。  
  
 ![3 &#45; 点透视图](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")  
  
 **3 点透视图**  
  
 ![1 &#45; 点透视图](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")  
  
 **1 点透视图**  
  
 大多数元素应朝或向右倾斜。  
  
 ![向右倾斜的图标](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")  
  
 仅当必要的清楚起见添加到对象时，请使用光源。  
  
|||  
|-|-|  
|**正确光源**|**不正确的光源**|  
|![正确的图标光源](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![不正确的图标光源](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|  
  
 使用轮廓，只是为了提高可读性较高或更好地传达隐喻。 负正 （深浅） 平衡应为 50/50。  
  
|||  
|-|-|  
|**轮廓的正确使用**|**使用不正确的轮廓**|  
|![正确的轮廓](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![不正确的轮廓](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>图标类型  
 **外壳和命令栏** 图标不能超过三个以下元素组成︰ 一个基准、 一个修饰符，一个操作或一个状态。  
  
 ![外壳和命令栏图标](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")  
  
 **外壳和命令栏图标的示例**  
  
 **工具窗口命令栏** 图标不能超过三个以下元素组成︰ 一个基准、 一个修饰符，一个操作或一个状态。  
  
 ![“工具”窗口命令栏图标](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")  
  
 **工具窗口命令栏图标的示例**  
  
 **树视图消歧器** 图标不能超过三个以下元素组成︰ 一个基准、 一个修饰符，一个操作或一个状态。  
  
 ![树视图消歧器图标](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")  
  
 **视图消歧器图标树中的示例**  
  
 **基于状态的值分类** 图标存在处于以下状态︰ 活动、 禁用，活动和非活动状态已禁用。  
  
 ![州/省和 #45; 基于的分类值图标](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")  
  
 **基于状态的值分类图标的示例**  
  
 **IntelliSense** 图标不能超过三个以下元素组成︰ 一个基准、 一个修饰符和一个状态。  
  
 !["IntelliSense" 图标](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")  
  
 **IntelliSense 图标的示例**  
  
 **小型 (16 x 16) 项目** 图标应具有不超过两个元素︰ 一个基准和一个修饰符。  
  
 ![16x16 项目图标 #40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 项目图标和 #40; 2 和 #41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 项目图标 &#40; 3 &#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")  
  
 **小型 (16 x 16) 项目图标的示例**  
  
 **大型 (32 x 32) 项目** 图标不能超过四个以下元素组成︰ 一个基准、 一到两个修饰符和覆盖的一种语言。  
  
 ![32x32“项目”图标](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")  
  
 **大型 (32 x 32) 项目图标的示例**  
  
### <a name="production-details"></a>生产详细信息  
 应使用 Windows Presentation Foundation (WPF) 创建所有新的 UI 元素和用于 WPF 的所有新图标应为以 32 位 PNG 格式。 24 位 PNG 是旧格式，不支持透明度，因此不建议用于图标。  
  
 保存 96 dpi 分辨率。  
  
#### <a name="file-types"></a>文件类型  
  
-   **32 位 PNG:** 图标的首选的格式。 一种无损数据压缩文件格式，可以将单个光栅 （像素） 图像存储。 32 位 PNG 文件支持阿尔法通道透明、 灰度校正和交错。  
  
-   **32 位 BMP:** 非 WPF 控件。 也称为 XP 或增强色，32 位 BMP 是 RGB/A 图像格式，阿尔法通道透明的真彩色图像。 Alpha 通道是一个层然后保存该位图作为其他 （第四个） 中的 Adobe Photoshop 中指定的透明度颜色通道。 所有 32 位 BMP 文件，以提供快速的可视提示有关的颜色深度为图稿生产期间添加黑色背景。 此黑色背景表示要屏蔽的用户界面中的区域。  
  
-   **32 位 ICO:** 项目图标和添加项。 所有 ICO 文件都是 32 位的阿尔法通道透明真彩色 (RGB/A)。 由于 ICO 文件可以存储多个大小和颜色深度，则 Vista 图标通常是 ICO 格式包含 16 x 16、 32 x 32、 48 x 48 和 256 x 256 映像大小。 为了在 Windows 资源管理器中正确显示，ICO 文件必须进行保存的向下到每个图像尺寸为 24 位和 8 位色深。  
  
-   **XAML:** 设计图面和 Windows 装饰器。 XAML 图标是支持缩放、 旋转、 归档和透明度的基于矢量的图像文件。 它们今天不是在 Visual Studio 中常见，但由于其灵活性而变得更受欢迎。  
  
-   **SVG**  
  
-   **24 位 BMP:** 为 Visual Studio 命令栏。 一种真彩色 RGB 图像格式，24 位 BMP 是透明的层将使用创建品红色 （R = 255，G = 0，B = 255） 作为拆装装置透明层的颜色键图标约定。 24 位 BMP 中使用的背景色显示洋红色的所有曲面。  
  
-   **24 位 GIF:** 为 Visual Studio 命令栏。 支持透明度真彩色 RGB 图像格式。 在向导图稿和 GIF 动画中通常使用 GIF 文件。  
  
### <a name="icon-construction"></a>图标构造  
 在 Visual Studio 中的最小图标大小为 16 x 16。 最大的共同使用为 32 x 32。 请记住不以填满整个 16 x 16、 24 x 24 或 32 x 32 框架，在设计一个图标。 清晰、 统一图标构造是必要的用户识别。 构建图标时，请遵守以下几点。  
  
-   图标应为清晰、 易于理解，且一致。  
  
-   最好是使用的状态通知元素作为单个图标而不是层叠在图标基元素。 在某些上下文中，UI 可能需要与基元素成对出现的状态元素。  
  
-   项目图标通常是包含几种大小的.ico 文件。 正在更新仅 16x16、 24x24 和 32x32 图标。 大多数 16 x 16 和 24x24 图标将包含相同的元素。 32x32 图标包含更多详细信息，包括项目语言类型时适用。  
  
-   32x32 图标基元素通常具有 2 个像素线条粗细。 1 或 2 像素线条粗细可用的详细信息元素中。 您最好的判断力用于确定哪一个是更适合。  
  
-   必须为 16 x 16 元素和 24x24 图标至少为 1 个像素宽间距。 对于 32 × 32 图标，使用 2 个像素之间以及修饰符和基元素之间元素的间距。  
  
 ![16x16、24x24 和 32x32 图标的元素间距](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")  
  
 **图标的元素间距尺寸 16x16、 24x24 和 32x32**  
  
#### <a name="color-and-accessibility"></a>颜色和辅助功能  
 Visual Studio 法规遵从性指导原则要求产品中的所有图标都传递颜色和对比度的可访问性要求。 这通过图标反转的方法，并在设计时，您应注意将反转在产品中的以编程方式。  
  
 在 Visual Studio 图标中使用的颜色的详细信息，请参阅 [在映像中使用颜色](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)。  
  
##  <a name="a-namebkmkusingcolorinimagesa-using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> 在映像中使用颜色  
  
### <a name="overview"></a>概述  
 在 Visual Studio 中的图标是主要单色。 保留颜色来传达特定信息并永远不会对修饰。 使用颜色︰  
  
-   若要指示某项操作  
  
-   状态通知向用户发出警报  
  
-   若要指定语言隶属关系  
  
-   若要区分 IntelliSense 中的项  
  
### <a name="accessibility"></a>可访问性  
 Visual Studio 法规遵从性准则要求，所有图标签都入到的产品传递颜色和对比度的可访问性要求。 中的 visual 语言调色板颜色已经过测试并满足这些要求。  
  
#### <a name="color-inversion-for-dark-themes"></a>深色主题的颜色反转  
 为了使图标显示为带有正确的 Visual Studio 深色主题中的对比度，反转以编程方式应用。 本指南中的颜色已选择部分，以便他们正确地反转。 向此调色板会限制使用的颜色或反转应用时，您将看到不可预知的结果。  
  
 ![颜色颠倒的图标的示例](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")  
  
 **具有已反转其颜色的图标的示例**  
  
### <a name="base-palette"></a>基调色板  
 所有标准图标包含三种基本的颜色。 图标包含没有渐变或投影 3D 工具图标的一个或两个例外情况。  
  
|用法|名称|值 （浅色主题）|样本|示例|  
|-----------|----------|---------------------------|------------|-------------|  
|背景/深|VS BG|424242 / 66,66,66|![样本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![基调色板示例](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|  
|前景/轻型|VS FG|F0EFF1 / 240,239,241|![样本 F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|轮廓|VS 出|F6F6F6 / 246,246,246|![样本 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 除了基本颜色以外的每个图标可能包含扩展的调色板中的一种其他颜色。  
  
### <a name="extended-palette"></a>扩展的调色板  
  
#### <a name="action-modifiers"></a>操作修改程序  
 下面的四个颜色表示所需操作的操作修改程序的类型︰  
  
|用法|名称|值 （所有主题）|样本|  
|-----------|----------|--------------------------|------------|  
|正|VS 操作绿色|388A34 / 56,138,52|![样本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|负数|VS 操作红色|A1260D / 161,38,13|![样本 A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|非特定|VS 操作蓝色|00539 C / 0,83,156|![样本 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|创建/新建|VS 操作橙色|C27D1A / 194,156,26|![样本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>示例  
 绿色用于肯定操作修饰符，如"添加"，"运行，""播放，"和"验证"。  
  
|||||  
|-|-|-|-|  
|![运行图标](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun") **运行**|![执行查询图标](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery") **执行查询**|![播放所有步骤图标](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps") **都播放所有步骤**|![添加控件图标](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl") **添加控件**|  
  
 红色用于负操作修改程序如"删除，""停止，""取消，"和"关闭"。  
  
|||||  
|-|-|-|-|  
|![删除关系图标](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship") **删除关系**|![删除列图标](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn") **删除列**|![停止查询图标](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery") **停止查询**|![连接离线图标](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline") **连接脱机**|  
  
 蓝色应用于非特定操作的最常见的修饰符表示为箭头，如"打开"状态，"下一步，""上一步，""导入"和"导出"。  
  
|||||  
|-|-|-|-|  
|![转到字段图标](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField") **转到字段**|![批处理复选 &#45; 在图标中](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn") **批处理签入**|![地址编辑器图标](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor") **地址编辑器**|![关联编辑器图标](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor") **关联编辑器**|  
  
 深色金牌主要用于"新建"修饰符。  
  
|||||  
|-|-|-|-|  
|![新建项目图标](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject") **新项目**|![创建新的图形图标](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph") **创建新关系图**|![新建单元测试图标](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest") **新单元测试**|![新建列表项图标](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem") **新列表项**|  
  
#### <a name="special-cases"></a>特殊情况  
 在特殊情况下，彩色的操作修饰符可能作为独立图标独立使用。 使用该图标的颜色反映了与关联的图标的操作。 这种用法仅限于的图标，包括一小部分︰  
  
||||||  
|-|-|-|-|-|  
|![运行图标](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun") **运行**|![停止图标](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop") **停止**|![删除图标](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete") **删除**|![保存图标](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save") **保存**|![导航后退图标](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack") **导航回**|  
  
### <a name="code-hierarchy-palette"></a>代码层次结构调色板  
  
#### <a name="folder"></a>文件夹  
  
|用法|名称|值 （所有主题）|样本|示例|  
|-----------|----------|--------------------------|------------|-------------|  
|文件夹|文件夹|DCB67A / 220,182,122|![样本 DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![“文件夹颜色”图标](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio 语言  
 每个通用的语言或 Visual Studio 中提供的平台都有关联的颜色。 基本图标，或在复合图标右上角中显示的语言修饰符，将使用这些色。  
  
|用法|名称|值 （所有主题）|样本|  
|-----------|----------|--------------------------|------------|  
|ASP，HTML，WPF|ASP HTML WPF 蓝色|0095D 7 / 0,149,215|![样本 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP 紫色|9B4F96 / 155,79,150|![样本 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS 绿色 （VS 操作绿色）|388A34 / 56,138,52|![样本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|CSS 红色|BD1E2D / 189,30,45|![样本 BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS 紫色|672878 / 103,40,120|![样本 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS 橙色|F16421 / 241,100,33|![样本 F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB 蓝色 （VS 操作蓝色）|00539 C / 0,83,156|![样本 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|TS 橙色|E04C06 / 224,76,6|![样本 E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|上一年度绿色|879636 / 135,150,54|![样本 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>图标具有语言修饰符的示例  
  
|||||||  
|-|-|-|-|-|-|  
|![Visual Basic 图标](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB") **VB**|![&#35;图标](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp") **C#**|![C# 43; &#43;图标](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus") **c + +**|![F &#35;图标](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp") **F #**|![JavaScript 图标](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript") **JavaScript**|![Python 图标](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python") **Python**|  
|![HTML 图标](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML") **HTML**|![WPF 图标](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF") **WPF**|![ASP 图标](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP") **ASP**|![CSS 图标](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS") **CSS**|![TypeScript 图标](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript") **TypeScript**||  
  
#### <a name="intellisense"></a>IntelliSense  
 IntelliSense 图标使用排他的调色板。 这些颜色用于帮助用户快速将智能感知的弹出列表中的不同项之间区分开来。  
  
|用法|名称|值 （所有主题）|样本|  
|-----------|----------|--------------------------|------------|  
|类中事件|VS 操作橙色|C27D1A / 194,125,26|![样本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|方法，模块中，委托的扩展方法|VS 操作紫色|652 D 90 / 101,45,144|![样本 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|域、 枚举项、 宏、 结构、 联合值类型，运算符，接口|VS 操作蓝色|00539 C / 0,83,156|![样本 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|对象|VS 操作绿色|388A34 / 56,138,52|![样本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|常量、 异常、 枚举项、 地图、 地图项、 Namespace，模板中，类型定义|背景 (VS BG)|424242 / 66,66,66|![样本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>IntelliSense 图标的示例  
  
||||||  
|-|-|-|-|-|  
|![IntelliSense 类图标](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass") **类**|![IntelliSense 私有事件图标](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **私有事件**|![IntelliSense 委托图标](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate") **委托**|![IntelliSense 方法好友图标](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **方法友元**|![字段图标](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field") **字段**|  
|![IntelliSense 受保护的枚举项图标](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **受保护的枚举项**|![IntelliSense 对象图标](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject") **对象**|![IntelliSense 模板图标](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate") **模板**|![IntelliSense 异常快捷方式图标](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut") **异常快捷方式**||  
  
### <a name="notifications"></a>通知  
 Visual Studio 中的通知用于指示状态。 通知调色板使用以下四种颜色，以及黑色或白色前景填充选项来定义具有以下状态级别的通知。  
  
|用法|名称|值 （所有主题）|样本|  
|-----------|----------|--------------------------|------------|  
|状态︰ 非特定语言|通知蓝色 （VS 蓝色）|1BA1E2 / 27,161,226|![样本 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|状态︰ 正数|通知绿色 （VS 绿色）|339933 / 51,153,51|![样本 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|状态︰ 负|通知红色 （VS 红色）|E51400 / 229,20,0|![样本 E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|状态︰ 警告|通知黄色 （VS 橙色）|FFCC00 / 255,204,0|![样本 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|前景色填充|通知黑色 （黑色）|000000 / 0,0,0|![样本 &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|前景色填充|通知空白 （白色）|FFFFFF / 255,255,255|![样本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>通知图标的示例  
  
|||||  
|-|-|-|-|  
|![警报图标](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert") **警报**|![警告图标](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning") **警告**|![完成图标](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete") **完成**|![停止图标](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop") **停止**|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 一般情况下，Visual Studio Online 功能组成托管在浏览器中。 在不同的环境颜色各不相同，但该样式将保持不变。  
  
|Group|用法|名称|值 （所有主题）|样本|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|背景|TFSO BG|656565/ 101, 101, 101|![样本 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|轮廓|TFSO 出|FFFFFF / 255，255，255|![样本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|背景|白色|FFFFFF / 255，255，255|![样本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|摩纳哥|背景|白色|FFFFFF / 255，255，255|![样本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|背景|白色|FFFFFF / 255，255，255|![样本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|正常|F12 Grey_Primary|555555 / 85, 85, 85|![样本 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|悬停|F12 Blue_Hover|2279BF / 34,121,191|![样本 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|已禁用|F12 LtGrey_Disabled|ABABAC / 171,171,172|![样本 ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|将鼠标指针悬停背景|将鼠标指针悬停 bg|D9EBF7 / 217,235,247|![样本 D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|按下的背景|按下的 bg|B2D7F0 / 178,215,240|![样本 B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|轮廓|VS 出|F6F6F6 / 246,246,246|![样本 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|信息|信息|00BCF2 / 0,188,242|![样本 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|警告|警告|F28300 / 242,131,0|![样本 F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|错误 / 负|Error_Negative|E81123 / 232,17,35|![样本 E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|启动 / 正数|Start_Positive|009E49 / 0,158,73|![样本 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|分页符类型|分页符类型|9B4F96 / 155,79,150|![样本 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|事件标记|事件标记|A51F00 / 165,31,0|![样本 A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|用户标记|用户标记|F16220 / 241,98,32|![样本 F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online 的图标的示例  
  
|TFS 联机||||  
|----------------|-|-|-|  
|![TFS Online 团队图标](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam") **Online 团队**|![TFS 信息图标](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation") **信息**|![TFS 历史记录图标](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory") **历史记录**|![TFS 分支图标](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch") **分支**|  
  
|Napa||||  
|----------|-|-|-|  
|![Napa 内容图标](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent") **内容**|![Napa 办公邮件图标](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail") **Office 邮件**|![Napa SharePoint 图标](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|![Napa 任务窗格图标](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane") **任务窗格**|  
  
|摩纳哥||||  
|------------|-|-|-|  
|![Monaco 文件图标](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles") **文件**|![Monaco Git 图标](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit") **Git**|![Monaco 搜索图标](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch") **搜索**|![Monaco 文本图标](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText") **文本**|  
  
|F12||||  
|---------|-|-|-|  
|![F12 整齐代码图标](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode") **相当代码**|![F12 警告图标](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning") **警告**|![F12 模拟图标](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate") **模拟**|