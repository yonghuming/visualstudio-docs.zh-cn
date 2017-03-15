---
title: "创建 Visual Studio 2017 RC 的脱机安装 | Microsoft Docs"
description: "了解如何创建 Visual Studio 的脱机安装。"
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>创建 Visual Studio 2017 RC 的脱机安装

## <a name="create-a-layout"></a>创建布局
如果想在另一台无法访问 Internet 的计算机上安装 [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/)，首先要创建一个包含所有必需的 Visual Studio 文件和组件的脱机安装布局。

然后可以使用所创建的脱机安装布局将 Visual Studio 安装到目标计算机中。     

> [!WARNING]
> 目前，Android SDK 不支持脱机安装体验。 如果在未连接到 Internet 的计算机上安装 Android SDK 安装程序项，则安装可能失败。 有关这一方面的详细信息，请转到本主题中的[脱机安装故障排除](#tshootofflineinstall)部分。


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>创建 Visual Studio 的脱机安装布局
1. 将 Visual Studio 安装程序可执行文件下载到本地计算机上的驱动器中。
  例如，[下载 vs_enterprise.exe 文件](https://www.visualstudio.com/vs/visual-studio-2017-rc/)。
2. 在命令提示符下使用以下参数（开关）运行 `vs_enterprise.exe`：

   a. 添加 `--layout <path>`，其中 `<path>` 是要将布局下载到的位置。 请注意，目前不支持相对路径（例如 `..\vs2017`）。 默认情况下会下载所有语言。 （请参阅示例 A。）

   b. 通过提供 `--lang <language>` 参数限制为仅下载一部分可用语言，其中 `<language>` 是一个或多个语言区域设置。  （请参阅示例 B 和示例 C。）

   c. 通过提供 `--add <package ID>` 参数限制为仅下载一部分工作负载和组件。 如此一来，只会下载指定的工作负载和组件（及其依赖项）。 （请参阅示例 D 和示例 E。）

   有关按 Visual Studio 产品排序的工作负载和组件 ID 的完整列表，请参阅我们的 [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids)（Visual Studio 2017 工作负载和组件 ID）页面。

### <a name="examples"></a>示例
**示例 A**：下载所有语言的所有工作负载和组件
  > ```vs_enterprise.exe --layout C:\vs2017```

**示例 B**：下载一种语言的所有工作负载和组件  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**示例 C**：下载多种语言的所有工作负载和组件
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**示例 D**：下载所有语言的一个工作负载
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**示例 E**：下载三种语言的两个工作负载和一个可选组件
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > 如果安装程序 .exe 文件名包含数字，则 --layout 参数将失败。 若要解决此问题，必须从文件名 &mdash; 中删除数字，例如，将 *vs_community__198521760.1486960229.exe* 重命名为 ***vs_community.exe***。

### <a name="language-locales"></a>语言区域设置

| 语言-区域设置 | 语言 |
| -----   | ----- |
| cs-CZ    | 捷克语 |
| de-DE    | 德语 |
| zh-CN    | 英语 |
| es-ES    | 西班牙语 |
| fr-FR    | 法语 |
| it-IT    | 意大利语 |
| ja-JP    | 日语 |
| ko-KR    | 朝鲜语 |
| pl-PL    | 波兰语 |
| pt-BR    | 葡萄牙语 - 巴西 |
| ru-RU    | 俄语 |
| tr-TR    | 土耳其语 |
| zh-CN    | 中文 - 简体 |
| zh-TW    | 中文 - 繁体 |


## <a name="install-from-a-layout"></a>从布局安装
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>从脱机安装布局安装 Visual Studio
1. 在目标计算机上，导航到“证书”文件夹，该文件夹位于“布局”文件夹中。
2. 右键单击并安装“证书”文件夹中的每个证书。

  （如果在安装证书后，系统提示输入密码，请单击“继续”。）  
3. 从“布局”文件夹运行 `vs_enterprise.exe`。

注意：如果要从部分布局进行安装，并且选择布局中不可用的工作负载、组件或语言，安装程序将尝试下载它们。  如果没有 Internet 访问权限，将无法安装这些项。

> [!CAUTION]
> 当前，脱机安装布局会创建一些具有受限权限 (ACL) 的文件，使部分用户无法访问。  在共享脱机安装*之前*，请确保调整权限 (ACL)，以便向其他用户授予读取访问权限。

## <a name="update-an-installation-layout"></a>更新安装布局
当 Visual Studio 2017 RC 有可用更新时，用户可以再次运行 `--layout` 命令，并指向同一布局文件夹，以确保该文件夹包含最新的组件。 系统只会下载自上一次运行 `--layout` 以来已更新的那些组件。

## <a id="tshootofflineinstall"> </a>安装布局故障排除
从脱机安装缓存进行脱机安装时，可能会看到提示无法安装某些组件和包的警告消息。 下表包含针对这些情况可能的解决方案。

| 组件或包 | 解决方案 |
| -------------------- | -------- |
|Android SDK 安装程序（API 级别）| 必须连接 Internet 才能安装 Android SDK（API 级别）包。 如果处于受限网络上，则在安装 Visual Studio 时必须允许访问以下 URL： <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>有关如何使用代理设置解决可能的问题的详细信息，请参阅 [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/)（使用代理时的 Visual Studio 安装故障（Android SDK 安装程序））博客文章。  |  

 > [!IMPORTANT]
 > 虽然一般情况下支持在生产环境中使用 Visual Studio 2017 RC，但安装 UI 中标记为“预览”的工作负载和组件不支持在生产环境中使用。

 ## <a name="see-also"></a>另请参阅
 * [安装 Visual Studio](install-visual-studio.md)
 * [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [报告 Visual Studio 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

