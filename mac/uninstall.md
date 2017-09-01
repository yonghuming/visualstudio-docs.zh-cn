---
title: "卸载 Visual Studio for Mac"
description: "卸载 Visual Studio for Mac 和相关工具的说明。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 6d021192e8104ec520aa057173d9dec41a62dfd3
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---

# <a name="uninstalling-visual-studio-for-mac"></a>卸载 Visual Studio for Mac

许多 Xamarin 产品支持跨平台应用程序开发，包括 Visual Studio for Mac 等独立应用。

本指南介绍了单独卸载每个产品的知识，可导航到相关部分查看。 遵循本指南中的全部指导，可卸载整个 Xamarin 工具集。

如果之前在计算机上安装了 Xamarin Studio，那么除了执行下面的步骤之外，可能还需按照 developer.xamarin.com 上的[卸载](https://developer.xamarin.com/guides/cross-platform/getting_started/installation/uninstalling_xamarin/)指南进行操作。

## <a name="uninstall-script"></a>卸载脚本

可通过使用位于[此处](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh)的卸载脚本，一次性卸载 Visual Studio 及其关联的组件。

卸载脚本中包含本文中出现的大部分命令。 由于可能存在外部依赖关系，脚本中忽略了两个主要部分：

- **卸载 Mono**
- **卸载 Android AVD**

要运行脚本，请执行以下操作：

1. 右键单击脚本，并选择“另存为...” 在 Mac 上保存文件。
2. 打开“终端”，并将工作目录更改为下载脚本的位置：

    ```bash
    $ cd /location/of/file
    ```
3. 使脚本可执行，并通过 **sudo** 运行它：

    ```bash
    $ chmod +x ./xamarin_uninstall.sh
    $ sudo ./xamarin_uninstall.sh
    ```
4. 最后，删除卸载脚本。

## <a name="uninstall-visual-studio-for-mac"></a>卸载 Visual Studio for Mac

从 Mac 中卸载 Visual Studio 的第一步是在 /Applications 目录中找到 Visual Studio.app，并将其拖动到回收站。 或者，单击右键，然后选择“移到回收站”，如下所示：

![将 Visual Studio 应用程序移动到回收站](media/uninstall-image1.png)

删除此应用程序包会删除 Visual Studio for Mac，尽管文件系统上仍有与 Xamarin 相关的其他文件。

要删除 Visual Studio for Mac 的所有痕迹，应在终端运行以下命令：

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf "~/Library/Preferences/Visual Studio"
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>卸载 Mono SDK (MDK)

Mono 是 Microsoft .NET Framework 的开放源代码实现，可供所有 Xamarin 产品（Xamarin.iOS、Xamarin.Android 和 Xamarin.Mac）使用，以便使用 C# 开发这些平台。

> [!WARNING]
> 除 Visual Studio for Mac 之外，还有其他应用程序使用 Mono，例如 Unity。
> 卸载 Mono 前，请确保 Mono 上没有其他依赖项。

若要从计算机删除 Mono Framework，请在终端运行以下命令：

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>卸载 Xamarin.Android

安装和使用 Xamarin.Android 需要许多必备项，例如 Android SDK 和 Java SDK。

使用以下命令删除 Xamarin.Android：

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>卸载 Android SDK 和 Java SDK

开发 Android 应用程序需要 Android SDK。 要完全删除 Android SDK 的所有部分，请在 ~/Library/Developer/Xamarin/ 中找到相关文件，并将其移到回收站。

不必卸载 Java SDK (JDK)，因为它已预先打包为 Mac OS X/macOS 一部分。

### <a name="uninstall-android-avd"></a>卸载 Android AVD

> [!WARNING]
> 除 Visual Studio for Mac 之外，还有其他应用程序使用 Android AVD 和这些附加 Android 组件，如 Android Studio。
> 删除此目录可能导致 Android Studio 中的项目中断。 

要删除任何 Android AVD 和附加 Android 组件，请使用以下命令：

```bash
rm -rf ~/.android
```

要仅删除 Android AVD，请使用以下命令：

```bash
rm -rf ~/.android/avd
```

 

## <a name="uninstall-xamarinios"></a>卸载 Xamarin.iOS

Xamarin.iOS 支持使用 C# 或 F# 通过 Visual Studio for Mac 开发 iOS 应用程序。

Xamarin 生成主机也是随早期版本的 Xamarin.iOS 自动安装的，以便在 Visual Studio 中进行 iOS 开发。 若要从计算机中卸载这二者，请遵循以下步骤：

在终端使用以下命令从文件系统删除所有 Xamarin.iOS 文件：

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>卸载 Xamarin.Mac

成功卸载 Visual Studio for Mac 后，可使用以下两个分别用于从 Mac 删除产品和许可证的命令从计算机删除 Xamarin.Mac：

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>卸载工作簿和检查器

从 1.2.2 开始，可通过运行以下命令从终端卸载 Xamarin Workbooks 和 Xamarin Inspector：

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

对于旧版本，需手动删除以下各项：

* 在 `"/Applications/Xamarin Workbooks.app"` 删除 Workbooks 应用
* 在 `"Applications/Xamarin Inspector.app"` 删除 Inspector 应用
* 删除加载项：`"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` 和 `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* 在 `/Library/Frameworks/Xamarin.Interactive.framework` 和 `/Library/Frameworks/Xamarin.Inspector.framework` 删除 Inspector 和支持文件

# <a name="uninstall-the-xamarin-profiler"></a>卸载 Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>卸载 Visual Studio 安装程序

使用以下命令删除 Xamarin 通用安装程序的所有痕迹：

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

