---
title: "Visual Studio for Mac 相较于 Xamarin Studio 的优势"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.translationtype: HT
ms.sourcegitcommit: f6c7e290f0abc2c32456e076420a7695ae868ba6
ms.openlocfilehash: 655795fd64958805e0137d7e231391c59f676776
ms.contentlocale: zh-cn
ms.lasthandoff: 09/07/2017

---

# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Visual Studio for Mac 相较于 Xamarin Studio 的优势 
 
在 Mac 上，Visual Studio for Mac 已经取代了 Xamarin Studio，成为功能完备的 IDE。 它提供的功能可用于开发 Web 应用和服务、跨平台移动和桌面应用及游戏。 此外，不论是要发布到 Azure，还是要创建 Azure Functions，它都可轻松实现与 Azure 的集成。 它能够满足你对现代 IDE 的所有期望，包括功能完备的源代码编辑器、功能强大的调试器、可自定义的工作区、Git 集成和丰富的扩展系统，都专为 Mac 本机设计。 

其他功能包括： 

* 基于 Roslyn 的 C# IntelliSense、重构、分析器和代码修复 
* 基于 NuGet 的程序包管理 
* 与 Visual Studio 兼容的项目格式 
* MSBuild 生成引擎 
* 集成单元测试 
* 对 F# 的支持 

本指南中列出的标记为“预览”的优势仅在 [alpha 通道](https://docs.microsoft.com/en-us/visualstudio/mac/update#Changing_the_Updater_channel)中可用。 

## <a name="language-support"></a>语言支持 

仅 Visual Studio for Mac 支持在 Mac 上编写 C# 7 代码。

## <a name="net-core"></a>.NET 核心  

[.NET Core](https://www.microsoft.com/net/core#macos) 平台可以创建在 Windows、Linux 和 Mac 上运行的应用程序。 Visual Studio for Mac 支持加载、创建、运行和调试 .NET Core 项目。 

.NET Core 随 Visual Studio for Mac 一同安装，现成可用。

.NET Core 支持包括： 

* C# 和 F# IntelliSense。 
* 控制台、库和 Web 应用程序的 .NET Core 项目模板。 
* 完整的调试支持，包括断点、调用堆栈、监视窗口等。 
* NuGet 包引用和基于 MSBuild 的还原。 
* 集成单元测试支持使用 .NET Core SDK 附带的 Visual Studio 测试平台进行运行和调试测试。 
* 从旧的 project.json 格式迁移。 
* .NET 标准项目支持。

## <a name="web-development"></a>Web 开发  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio for Mac 包括适用于 MVC 和 Web API 的现成 ASP.NET Core 模板。
 
![HTML IntelliSense](media/benefits-vsmac-over-xs-image3.png)

Visual Studio for Mac 还添加了针对 HTML、CSS 和 JSON 文件的新 Web 工具支持。 

### <a name="html"></a>HTML 

* 新的 HTML 模板。 
* 改进的智能缩进和格式设置。 
* 改进的着色处理功能。 
* 改进的 IntelliSense。 
* 代码折叠（必须启用）。 
* Unminify 命令。 
* 改进的代码模板（片段）。 
* 使用 `<div>` 环绕选定内容。 
* 可以将选定文本向上/向下移动的向上/向下选项。 

### <a name="css"></a>CSS 

* 改进的智能缩进和格式设置。 
* 改进的着色处理功能。 
* 改进的 IntelliSense。 
* 代码折叠。 
* 多个代码模板（片段）。 
* 可以将选定文本向上/向下移动的向上/向下选项。 

### <a name="json"></a>JSON 
* 有权访问 schemastore.org 的架构选择器。 
* 从架构进行验证。 
* 从架构进行 IntelliSense。 
* 改进的智能缩进和格式设置。 
* 改进的着色处理功能。 
* 注释/取消注释。 
* 引号注入和大括号匹配。 
* 可以将选定文本向上/向下移动的向上/向下选项。 

## <a name="publishing-to-azure"></a>发布到 Azure

通过 Visual Studio for Mac，可将 ASP.NET Core Web 应用和服务发布到 Azure App Service。 

![发布到 Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Azure Functions（预览）

Azure Functions 是一个在云中轻松运行小段代码或函数的解决方案。 可通过 Visual Studio for Mac 对 Azure Functions 进行编码和本地调试。 要开始操作，请在“新建项目”对话框中的“云”下查找 Azure Functions。 

### <a name="docker-support-preview"></a>Docker 支持（预览）

可将 ASP.NET Core 应用发布到 Docker 容器，并从 Azure App Service 运行这些应用。 

要在项目中启用 Docker 支持，请右键单击 ASP.NET Core Web 应用，并选择“添加”>“添加 Docker 支持”。 

要将 Web 应用发布到 Docker 容器，请使用 Visual Studio for Mac 中引入的“发布”>“发布到 Azure”工作流。

## <a name="source-editor-improvements"></a>源编辑器改进 

除了基于 Roslyn 的 C# IntelliSense、重构、分析器和代码修复外，Visual Studio for Mac 源编辑器相较于 Xamarin Studio 还具有以下改进： 

### <a name="language-bundles"></a>语言包 

Visual Studio for Mac 支持 TextMate (`.tmBundle`) 和 sublime 3 (`.sublime`) 语言包，可使用这些语言包添加： 

* 编辑器颜色主题 
* 代码片段 
* 新语言的语法，启用突出显示以及基本 IntelliSense 

可以在“首选项”>“文本编辑器”>“语言包”中添加这些捆绑包。 

### <a name="color-theme-support"></a>颜色主题支持 

Visual Studio for Mac 支持以下颜色主题格式： 

* Visual Studio (`.vssettings`) 
* Xamarin studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) 是一个游戏创建工具，可用于针对所有主要平台（移动、桌面、游戏主机、AR和 VR设备甚至网页）创建高质量的跨平台 2D 和 3D 游戏。 

从 Unity 5.6.1 开始，可使用 Visual Studio for Mac 编写和调试 Unity 游戏。 要开始操作，请将 Visual Studio 设置为 Unity 5.6.1 脚本编辑器。 

Tools for Unity 包括： 

* 对用 C# 编写的脚本的支持。 
* Unity Solution Pad。 
* Unity 编辑器一键调试。 
* 针对 Unity 消息的 IntelliSense。 
* Unity 着色器的代码着色功能。 
* Unity 文档访问。 

## <a name="xamarin"></a>Xamarin 

Xamarin 跨平台功能始终是 Xamarin Studio 的首要功能，但一些 Xamarin 功能仅在 Visual Studio for Mac 中可用 

### <a name="android"></a>Android 

* [Android SDK 管理器](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* 仅 Visual Studio for Mac 支持 Android O，Xamarin Studio 不支持 

### <a name="ios-and-mac"></a>iOS 和 Mac 

* [iOS 签名工作流更新](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * 创建签名标识，并将它们安装到本地 Keychain。 
    * 创建预配配置文件。 
    * 向现有配置文件添加签名标识。
    *  预配设备：在 Apple 开发者门户中注册设备，并将它们添加到预配配置文件。
* 仅 Visual Studio for Mac 支持 iOS 11、watchOS 4、和 tvOS 2，Xamarin Studio 不支持 
* 仅 Visual Studio for Mac 支持 MacOS High Sierra，Xamarin Studio 不支持 

### <a name="cross-platform"></a>跨平台 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/)（预览） 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/)（预览） 
 
