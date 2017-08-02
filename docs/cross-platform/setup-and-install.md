---
title: "设置和安装 | Microsoft Docs"
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d353d8a0a41ad487191b79aa68f26585cf9902b4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="setup-and-install"></a>设置和安装
要使用 Xamarin 从常见的 C#/.NET 代码基础生成本机 iOS、Android 和 Windows 应用，你需要具备以下项目：  
  
-   若要生成 Windows 和 Android 应用：需要有安装了 Visual Studio 2017 或 2015 和 Xamarin 的 Windows 开发计算机。 还可按照 [Xamarin 直接安装](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) 中的说明操作，使用 Visual Studio 2013。 
  
-   若要生成 iOS 应用：需要有安装了 XCode 和 Xamarin 且操作系统为 macOS Sierra 10.12 或更高版本的 Mac。  
  
 可同时设置 Windows 和 Mac 计算机，在这些安装程序运行期间，可通过[了解如何使用 Xamarin 进行移动开发](../cross-platform/learn-about-mobile-development-with-xamarin.md)阅读和观看必要的背景材料。  
 
如果在执行此设置和安装后使用 Xamarin 时遇到问题，请在 [ forums.xamarin.com](http://forums.xamarin.com/) 上发布你的问题。
  
> [!NOTE]
>  自 2016 年 3 月 31 日起，所有版本的 Visual Studio 中均随附所有 Xamarin，无需额外费用，且不需要单独的许可证。 Xamarin Studio Community for Mac 向学生、OSS 开发者和小型团队免费提供。 请注意，对于使用早期 Xamarin 许可证配置的 Visual Studio 现有安装，必须将 Xamarin 更新到版本 4.0.3.214 或更高版本。 为此，请转到“工具”>“选项”>“Xamarin”>“其他”，单击“立即检查”链接，然后下载 4.0.3.214 更新。 重启 Visual Studio 时，请转到“工具”>“Xamarin 帐户...”，然后应会看到更新后的状态。  
  
##  <a name="prereq"></a> 先决条件  
  
###  <a name="for-targeting-windows-and-android"></a>若要定位 Windows 和 Android 
  
1.  建议：使用运行 Windows 8 或更高版本的物理 Windows 计算机（而非 VM），以获得最佳的 Android 仿真器性能。 （我们是否提到过你需要物理计算机而不是 VM？）  
  
2.  可使用带 Windows 7 或更早版本的计算机，此时会将 Xamarin Player 用作 Android 仿真程序。 
    
3. 无论哪种配置，均直接在连接的物理设备上直接运行应用。  
  
### <a name="for-targeting-ios"></a>若要定位 iOS  
  
1.  使用联网的 Mac 或 Mac mini，操作系统为 macOS Sierra 10.12 或更高版本（Xcode 8.3 所必需）。  
  
2.  在 Windows (7+) 计算机上使用 Visual Studio 作为主要开发环境时，联网的 Mac 只需要编译和调试 iOS 应用、附加到 iOS 模拟器或受限设备，并使用 Visual Studio 中的情节提要设计器进行用户界面设计。 较早的 Mac 型号完全可满足此辅助角色的需求。  
  
##  <a name="windows"></a> Windows 设置（Visual Studio 和 Xamarin）  
  
> [!TIP]
>  这些说明适用于 Visual Studio 2017。 对于 Visual Studio 2015，请参阅 [MSDN](https://msdn.microsoft.com/en-us/library/mt613162.aspx)。 若要在 Visual Studio 2013 中使用 Xamarin（需要 Update 2），请按照 [ Xamarin 直接安装](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) 的说明操作。  
  
1.  [下载并启动 Visual Studio 2017 任意版本（Community、Professional 或 Enterprise）的安装程序](https://www.visualstudio.com/downloads/)。 Visual Studio 2017 Community 是免费版本；Professional 和 Enterprise 版本可免费试用 30 天，30 天后需购买许可证。  
  
    1.  如果已安装 Visual Studio 2017，请通过“开始”菜单运行“Visual Studio 安装程序”。
  
2.  在安装程序中，单击“启动”_旁边_的“其他选项”（三横杠图标）按钮，然后选择“修改”：  
  
     ![选择 Visual Studio 安装程序中的“修改”选项](~/cross-platform/media/cross-plat-xamarin-setup-1a.png "跨平台 Xamarin 安装 1")  
  
3.  选中以下选框：  
  
    1.  “移动和游戏”>“使用 .NET 的移动环境”。 这也将自动选择“常用工具和软件开发工具包”下的各种 Android 工具。 此选项还应更新现有的所有 Xamarin 安装。  
  
         ![选择“游戏和移动开发”下的“移动开发”选项](~/cross-platform/media/cross-plat-xamarin-setup-2a.png "跨平台 Xamarin 安装 2")  
  
    2. （可选）“Windows”>“通用 Windows 平台开发”。 这包括用于安装需要较长时间下载的仿真器映像的选项；稍后可以随时返回 Visual Studio 安装程序进行添加。 
  
4.  单击“修改”按钮，让进程运行起来。 同样，这将需要一些时间才能完成，在此期间可继续查看 Mac 安装说明并浏览[了解如何使用 Xamarin 进行移动开发](../cross-platform/learn-about-mobile-development-with-xamarin.md)。  
  
5.  安装完成后，请启动 Visual Studio 并在系统提示时使用你的 Microsoft 帐户进行登录（此帐户即用于 Windows 的帐户）。  
      
6.  若要测试 Android 应用，请使用 [Android SDK 仿真器](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/)（如果没有物理设备的话）。 请参见下面的注释。  
  
 Windows 计算机上模拟器的相关备注：CPU 一次仅支持一种虚拟化技术，因此最好只在开发计算机上采用一种技术。 有 3 种主要的虚拟化技术，分别是：Hyper-V（由适用于 Android 的 Visual Studio 模拟器和 Windows Phone 模拟器使用）、Virtual Box（由 Genymotion 使用）和 Intel HAXM（由 Android SDK 模拟器使用）。 由于 Hyper-V 和 Virtual Box 之间的各种问题，最好在任意给定计算机上仅使用一种模拟器，因此建议在 Windows 8 和更高版本的计算机上使用 Hyper-V，在 Windows 7 和更早版本上以及在 Mac 上运行 Windows 时使用 Intel HAXM 模拟器。  
  
##  <a name="mac"></a>Mac 设置（Apple ID、Xcode 和 Xamarin）  
  
1.  如果尚无 Apple ID，请在 [https://appleid.apple.com](https://appleid.apple.com/) 处创建免费 Apple ID。 这是安装和登录 Xcode 所必需的。  
  
2.  从  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)处下载并安装 Xcode，并如 [将帐户添加到 XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) 中所述添加你的 Apple ID。  
  
3.  按照 [安装和配置 Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com) 上的说明下载和安装 Xamarin。  
  
4.  在 Windows 和 Mac 计算机上安装好 Xamarin 后，请按照[连接到 Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com) 上的说明操作，以便可通过 Windows 计算机上的 Visual Studio 针对 iOS 和 Mac 进行开发。  
  
     请注意，这两台计算机必须位于同一本地网络。
