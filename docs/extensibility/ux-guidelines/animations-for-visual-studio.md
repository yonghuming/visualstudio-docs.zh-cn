---
title: "Visual Studio 的动画 |Microsoft 文档"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: b36b5e35758ad10109328d6f001e043ad7dcbe15
ms.contentlocale: zh-cn
ms.lasthandoff: 05/04/2017

---
# <a name="animations-for-visual-studio"></a>Visual Studio 的动画
## <a name="animation-fundamentals"></a>动画基础知识  
  
### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio 中的动画最佳做法  
遵循这些规则，以确保 Visual Studio IDE 之间的一致和用户友好动画样式。  
  
-   **应慎重选择。** 限制为那些有特定用途的动画。  
  
-   **计时和速度很重要**以确保转换认为快速而自然︰  
  
    -   完成动态显示内半秒 （500 毫秒） 的转换。  
  
    -   需要快速，它们不会中断用户的工作流将频繁发生的动画。 观察循环中的动画并调整计时，直到它的外观右。 
  
    -   因此快速或快很难以理解，但不是速度很慢，它可以使一个耐心转换完成，不应为动画。  
  
    -   使用变量计时强调重要性。 例如，当在类图上的项的序列中导航，项之间的转换通过速度然后速度下降，以专注于重要的项。  
  
-   **使用逐步非线性缓动**从一个状态到另一个中，提供一种安静、 更自然的移动。  
  
-   如果可能，**悬停时使用细微动画**以指示在鼠标交互元素。  
  
-   如果你依赖于动画中你的功能，然后**提供一种方式来将其关闭**本地 （对于所有功能） 中的一个选项作为**工具 > 选项**对话框。  
  
-   **只有一个动画应发生一次**，传达只是一条信息。 移动或尝试传递多个操作的多个对象可以是令人困惑。 
  
-   **种微妙很重要。** 在大多数情况下，动画并不一定需要用户采取行动，以提供其用途。 在计时、 排序、 和行为细微的更改可能会严重影响感知，并且可以使有效和无效动画之间的差异。  
  
-   当使用动画吸引人们关注一些，**确保它是值得中断用户**的思路。  
  
-   **显示进度或状态时**动画通过︰  
  
    -   停止显示进度移动时的基础进程不向前移动。 
  
    -   将不确定的进程与确定进程区分开来。  
  
    -   请确保动画具有身份的完成和失败状态。  
  
    -   最小化使用的效果动画，显示状态并确保它们具有真正的价值，所提供的实际使用的其他信息。 示例包括暂时性的状态更改和突发事件  
  
#### <a name="animation-donts"></a>动画注意事项︰
  
-   不要使用小动作数 （中内存占用较小的移动）。 首选淡化和推移移动对象发生更改。  
  
-   不要使用屏幕的实际空间较大区域上发生的动画。 而不考虑大小，这种样式是动画的让人分散注意力给用户。  
  
-   不要使用动画且不与当前侧重于用户的对象相关或与之进行交互。  
  
-   不要使用需要用户交互才能重置的状态，如强制用户响应以使其停止闪烁闪烁通知的动画。 与其进行交互以任何方式应足以关闭它们。  
  
有关这些最佳实践的应用程序的详细信息，请参阅[动画模式](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)。  
  
### <a name="animation-metrics"></a>动画度量值  
  
-   系统应明显反映以小于 10 毫秒为单位的用户笔势。  
  
-   动画的转换不应需要超过 500 毫秒才能完成。  
  
-   补偿的转换，需要更长的时间的一种方法是将其分隔成两个部分。 例如，一种动画效果的第一部分无法作为空内容容器 （最多 500 毫秒为单位），内容淡入淡出跟到容器 （最多 500 毫秒为单位）。  
  
-   对于可以计算的加载时间，是首选决定进度指示器 （-完成百分比的进度指示器）。  
  
-   为无法计算的加载时间，如光标或嵌入的旋转动画 （加载或工作指示器） 忙指示器适合。  
  
### <a name="animation-as-communicator"></a>作为 communicator 的动画  
在 Visual Studio UI 中，动画函数只能用作通信工具。  它用于通信的各种信息，例如在 UI 中 （例如，当菜单打开或关闭） 的结构更改。 动画可帮助实现可视化效果的复杂系统，如安装进度可视化效果的系统时间相关的行为。 动画还可以用于吸引通过警报和通知的关注。  
  
 UI 动画通常函数通过四种方法︰ 可视化、 吸引注意力、 模拟，和响应时间/进度指示器。  
  
#### <a name="visualize"></a>可视化  
动画可以强调对象的三维性质，并使用户更轻松地直观显示其空间的结构。 若要实现此目的，动画可能需要启动一个完整的圆中的对象渐变反复，将其将对象更接近和或略有增加其大小以强调滚动更新或焦点。  
  
尽管三维可能将对象移动与用户控件 （以编程方式或手动安装），在设计器应提前确定如何发挥最佳动画提供了对对象的最佳了解移动。 此编程动画可以，然后将激活的用户通过将光标放在上的对象，而用户控制动作数要求用户了解如何操作对象。 限制到单个轴或一次; 方向移动可以缩放、 旋转，或转换，但不同时执行多个。  
  
可视化类别包括的数据、 关系、 状态，方面结构、 序列和时间。  
  
##### <a name="data"></a>数据  
说明了复杂和变量信息︰  
  
-   如图表和图形信息可视化效果间移动  
  
-   浏览一系列单步执行、 指导的教程，和分页  
  
-   调用扩展详细信息，指向，并突出显示的特定信息  
  
-   覆盖详细信息以及在具有焦点的元素之上的其他信息
  
-   到另一个变形从一种结构化或组织的表示形式  
  
-   随着使用时间滑块、 角快速轮和传输控件 （播放、 停止和暂停） 的时间的推移表示更改 
  
##### <a name="relationships"></a>关系  
  
-   说明项之间的相互或哪些项与给定项相关
  
-   显示层次结构和父子或同级关系
  
-   一个元素生成另一个
  
-   一个元素最大程度减少到另一个元素
  
-   受限的到另一个元素
  
##### <a name="state"></a>状态  
  
-   内容更新
  
-   用户焦点和所选内容  
  
-   进度  
  
-   错误  
  
##### <a name="structure"></a>结构  
  
-   正在切换一个节点上的结构  
  
-   重定向  
  
-   最小化和最大化，或展开和折叠  
  
##### <a name="sequence"></a>序列  
  
-   幻灯片放映序列  
  
-   逐一浏览图片  
  
##### <a name="time"></a>时间  
  
-   显示随时间、 时间间隔和段视频  
  
-   移到回收站、 撤消和重做  
  
-   还原历史状态  
  
#### <a name="attract-attention"></a>引起关注  
如果目标是以用户的引起对单个带多个元素，或更新的信息向用户发出警报，动画可能合适。 例如，你的应用程序起始页可能采用滑入到位，在页面加载之后的入门按钮。  
  
一般来说，在屏幕上的最后一个移动元素方面吸引用户的关注。  在动画元素的序列中，用户的关注将遵循的最后一个移动对象。  
  
##### <a name="alert"></a>警报  
  
-   向用户发出警报、 获取关注、 显示进度  
  
-   显示，内容正在完成的正确或不正确或显示进度或进行更改  
  
-   任务，如查找的详细联机信息，或了解当前任务执行期间提示用户  
  
##### <a name="notifications"></a>通知  
  
-   用户的错误条件发出警报  
  
-   中断用户查看是否他们想要其他事情  
  
-   轻轻地通知用户进程已完成或发生更改时，在下载已完成。  
  
#### <a name="simulate"></a>模拟  
此类别包括 physicality 和维数。  
  
-   说明对象来自或它们转到  
  
-   展开和折叠或打开和关闭  
  
-   平移、 滚动、 和页将变为  
  
-   堆叠和 z 顺序  
  
-   传送和 accordion  
  
-   翻转和旋转 UI  
  
#### <a name="response-and-progress-indicators"></a>响应和进度指示器  
进度指示器有几个值得注意的优点︰  
  
-   这两个确定和不确定的进度指示器打消疑虑系统未损坏，并着手解决的问题的用户。  
  
-   确定指示器授予的用户的多久完成操作的意义上时的进展情况，以及获取接近完成的感觉。  
  
##  <a name="BKMK_AnimationPatterns"></a>动画模式  
  
### <a name="overview"></a>概述  
Visual Studio 中的动画是为了提供一种特定功能而不影响用户工作效率。 通常情况下，Visual Studio 中的动画应为︰  
  
-   小型和非介入式  
  
-   自然而真实  
  
-   难以捉摸也最 subdued  
  
-   快速、 高效地  
  
-   宽松的不名匆忙之中  
  
此图显示了 Visual Studio 建议动画样式。 最常使用任何动画或细微动画像淡入 / 淡出。 有限的应用程序的移动动画一样进行扩展和收缩，X 和 Y 位置更改和旋转。 
  
![Visual Studio 的建议的动画样式](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio 的建议动画样式
  
#### <a name="appear-and-disappear"></a>出现和消失  
使用此模式中，元素会从切换可见到扩展的视图和回不过渡动画。  
  
![出现和消失动画](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />出现和消失动画  
  
##### <a name="correct-usage"></a>正确使用  
需要立即显示或消失，以便用户不将注意力集中也不受阻全新 UI 元素。 此外，缓慢移动的动画可能无妨性能拖动、 使用出现和消失样式不会发生这种情况。  
  
##### <a name="incorrect-usage"></a>用法不正确  
在其中的 UI 显示方式突然用户具有不知道发生了什么情况，并添加动画与上下文的理解将帮助的用例。  
  
##### <a name="animation-properties"></a>动画的属性  
时间延迟通常为 0 秒。  
  
##### <a name="examples"></a>示例    
-   自动隐藏工具窗口  
  
-   键盘激活编辑器 UI 中，如 IntelliSense 和参数帮助  
  
-   展开/折叠代码区域  
  
#### <a name="fade-in-and-fade-out"></a>淡入和淡出  
UI 元素不可见 （0%不透明度） 从使用此模式中，代码转换为可见 （100%不透明度），反之亦然。  
  
![淡入和淡出动画](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />淡入和淡出动画  
  
##### <a name="correct-usage"></a>正确使用  
这是最常用建议 UI 动画。 它是而不会中断流添加感兴趣的微妙效果。 在某些情况下，用户可能没有意识到没有动画，觉察平滑流并流动 UI 系统。  
  
##### <a name="animation-properties"></a>动画的属性  
  
-   启动不透明度︰ 淡的 0%、 淡出的 100%  
  
-   结束不透明度︰ 淡的 100%，淡的 0%  
  
-   持续时间︰ 200 毫秒独立，100 毫秒时用作组合动画序列的一部分  
  
-   缓动样式︰ 正弦 InOut  
  
##### <a name="examples"></a>示例  
  
-   自动隐藏工具窗口  
  
-   菜单打开和关闭  
  
-   前景色和背景选项卡转换  
  
#### <a name="color-blend-from-a-to-b"></a>从 A 到 B 的颜色混合  
UI 元素组装在此模式中，它更改颜色 A 为颜色 b。  
  
![颜色混合动画](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />颜色混合动画  
  
##### <a name="correct-usage"></a>正确使用  
与在 UI 元素到另一个从一个上下文或状态更改颜色动画转换。  
  
##### <a name="animation-properties"></a>动画的属性  
  
-   开始颜色︰ 特定于用户界面的  
  
-   结束颜色︰ 特定于用户界面的  
  
-   持续时间︰ 200 毫秒独立，100 毫秒时用作组合动画序列的一部分  
  
-   缓动样式︰ 正弦 InOut  
  
##### <a name="examples"></a>示例  
  
-   文档窗口状态转换 (处于活动状态，最后一个活动，和非活动)  
  
-   工具窗口状态转换 （变得精准而失去焦点）  
  
#### <a name="expand-and-contract"></a>扩展和收缩  
使用此模式中，UI 元素 X，Y 或两个方向中展开。  
  
![扩展和收缩动画](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />扩展和收缩动画  
  
##### <a name="correct-usage"></a>正确使用  
与在 UI 元素到另一个上下文从更改大小，经过动画处理的转换。  
  
##### <a name="animation-properties"></a>动画的属性  
  
-   倍的规模: %或特定的尺寸 （以像素为单位）  
  
-   Y 缩放: %或特定的尺寸 （以像素为单位）  
  
-   定位点位置︰ 通常左上角 （用于从左到右语言） 或 （对于从右向左的语言） 的右上角  
  
-   持续时间︰ 200 毫秒独立，100 毫秒时用作组合动画序列的一部分  
  
##### <a name="examples"></a>示例  
  
-   体系结构资源管理器面板展开和折叠  
  
-   起始的页项目展开和折叠  
  
#### <a name="x-y-position-change"></a>X，Y 位置更改  
使用此模式中，UI 元素更改和 / 或其 X 或 Y 位置。  
  
![X，Y 位置更改动画](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X，Y 位置更改动画  
  
##### <a name="correct-usage"></a>正确使用  
与在 UI 元素到另一个上下文从更改位置动画转换。  
  
##### <a name="animation-properties"></a>动画的属性  
  
-   启动 X 和 Y 位置︰ 特定于用户界面的  
  
-   结束 X 和 Y 位置︰ 特定于用户界面的  
  
-   运动路径︰ 无  
  
-   持续时间︰ 200 毫秒独立，100 毫秒时用作组合动画序列的一部分  
  
-   缓动样式︰ 正弦 InOut  
  
##### <a name="example"></a>示例  
选项卡重新排序  
  
#### <a name="rotate"></a>旋转  
使用此模式中，UI 元素将旋转。  
  
![UI 元素旋转动画](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />UI 元素旋转动画  
  
##### <a name="correct-usage"></a>正确使用  
仅对不确定旋转进度指示器。  
  
##### <a name="animation-properties"></a>动画的属性  
  
-   旋转度数︰ 360  
  
-   旋转中心︰ 中间的对象  
  
-   持续时间︰ 连续  
  
##### <a name="example"></a>示例  
不确定的进度指示器 （旋转）  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>常见的命令行程序 UI 操作和建议的动画  
  
#### <a name="tab-open"></a>选项卡上打开  
![选项卡打开动画](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />选项卡打开动画  
    
-   样式︰ 显示  
  
-   零秒持续时间︰  

#### <a name="tab-close"></a>选项卡关闭  
![选项卡关闭动画](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />选项卡关闭动画  
  
-   样式︰ X 位置更改  
  
-   持续时间︰ 200 毫秒  
  
#### <a name="tab-reorder"></a>选项卡重新排序  
![Visual Studio 中的选项卡重新排序动画](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />选项卡重新排序动画

-   样式︰ X 位置更改  
  
-   持续时间︰ 200 毫秒  
    
#### <a name="close-floating-document"></a>关闭浮动文档  
![关闭浮动文档动画](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />关闭浮动文档动画  
   
-   样式︰ 显示  
  
-   持续时间︰ 200 毫秒   
 
#### <a name="window-state-transition"></a>窗口状态转换  
![窗口状态过渡动画](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />窗口状态过渡动画  
    
-   样式︰ 若要与其他 windows 保持一致，让当前操作系统定义文档关闭动画。  
  
-   持续时间︰ 200 毫秒  
  
#### <a name="menu-open"></a>打开菜单  
![菜单打开动画](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />菜单打开动画  
    
-   样式︰ 淡  
  
-   持续时间︰ 200 毫秒  
  
#### <a name="menu-close"></a>关闭菜单  
![菜单关闭动画](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />菜单关闭动画  
    
-   样式︰ 淡  
  
-   持续时间︰ 200 毫秒  
  
#### <a name="auto-hide-tool-window-reveal"></a>自动隐藏工具窗口显示  
![自动隐藏工具窗口显示动画](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />自动隐藏工具窗口显示动画  

-   样式︰ 显示  
  
-   零秒持续时间︰
