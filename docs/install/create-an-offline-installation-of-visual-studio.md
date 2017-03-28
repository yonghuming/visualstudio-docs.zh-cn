---
title: "创建 Visual Studio 2017 的脱机安装程序 | Microsoft Docs"
description: "了解如何创建 Visual Studio 的脱机安装程序。"
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
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
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: 563c78a49eb55886b1ddbd4f437951c99c6568e5
ms.lasthandoff: 03/22/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>创建 Visual Studio 2017 的脱机安装程序
我们了解很多客户希望使用 [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067) 的脱机安装程序。 尽管我们不提供 ISO 映像，但很容易创建在脱机情况下用于安装的文件夹。

操作方法如下。

## <a name="download-the-setup-file-you-want"></a>下载所需安装程序文件
**[下载](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)**所需 Visual Studio 版本。 请确保单击“保存”，然后单击“打开文件夹”。

安装程序文件&mdash;或更具体点，引导程序文件&mdash;将与下面其中一项匹配。

|版本 | 文件|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Visual Studio 社区 |**vs_community.exe**|

其他受支持的引导程序包括 vs_buildtools.exe、vs_feedbackclient.exe、vs_teamexplorer.exe、vs_testagent.exe、vs_testcontroller.exe 和 vs_testprofessional.exe。

## <a name="create-an-offline-installation-folder"></a>创建脱机安装文件夹
若要创建含所有语言和所有功能的脱机安装，请使用下面示例中的命令之一。

（请确保从下载目录运行该命令。 通常情况下，在运行 Windows 10 的计算机上为：`C:\Users\<username>\Downloads`）。

- 对于 Visual Studio Enterprise，请运行： <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- 对于 Visual Studio Professional，请运行： <br> ```vs_professional.exe --layout c:\vs2017offline```
- 对于 Visual Studio Community，请运行： <br> ```vs_community.exe --layout c:\vs2017offline```

有关更多示例，请参阅本页的[如何自定义脱机安装程序](#how-to-customize-your-offline- installer)部分。

## <a name="install-from-the-offline-installation-folder"></a>从脱机安装文件夹安装
立即或以后运行脱机安装；由你决定。 但在执行时，请按照下列步骤操作。

  1. 安装证书（它们位于“布局”文件夹中的“证书”文件夹中。 只需右键单击每个证书即可安装）。

  2. 运行安装文件。 例如，运行： <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>脱机安装程序的其他提示
自定义或更新脱机安装程序很容易；以下是相关说明。 如果脱机安装程序出现问题，我们也为你提供了故障排除和支持信息。

### <a name="how-to-customize-your-offline-installer"></a>如何自定义脱机安装程序
可通过多种方法自定义脱机安装程序。 以下是如何通过[语言区域设置](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)对其进行自定义的几个示例。

 - 若要下载仅一种语言的所有工作负载和组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - 若要下载多种语言的所有工作负载和组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - 若要下载所有语言的一个工作负载，请运行 <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - 若要下载三种语言的两个工作负载和一个可选组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```若要深入了解可用于自定义安装的选项，请参阅[使用命令行参数安装 Visual Studio 2017 ](use-command-line-parameters-to-install-visual-studio.md)页。


### <a name="how-to-update-an-offline-installer"></a>如何更新脱机安装程序
你可能需要在以后更新脱机安装程序。 操作方法如下。
* 若要更新从脱机安装文件夹安装的 Visual Studio 实例，请运行 Visual Studio 安装程序，然后单击“更新”。
* 若要刷新脱机安装文件夹，以使其包括最新更新，请再次运行 ```--layout``` 命令。 请确保指向之前使用的同一个文件夹；这样一来，将仅下载上次运行 ```--layout``` 后更新的组件。


### <a name="how-to-troubleshoot-an-offline-installer"></a>如何解决脱机安装程序问题
有时会出现问题。 以下是有关已知问题和有用的解决方案的表格。

| 问题       | 项                   | 解决方案 |
| ----------- | ---------------------- | -------- |
| 你将收到一条警告消息，指示无法安装某些组件和包。  | Android SDK 安装程序（API 级别） | 如果想要包含 Android SDK（API 级别）包，创建脱机安装程序时必须可连接 Internet。 如果网络受限，则必须允许访问以下 URL： <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>有关如何使用代理设置解决可能的问题的详细信息，请参阅 [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/)（使用代理时的 Visual Studio 安装故障（Android SDK 安装程序））博客文章。  |  
| 用户没有访问文件的权限。 | 权限 (ACL) | 请确保调整权限 (ACL)，以便他们在共享脱机安装前先向其他用户授予“读取”权限。 |
| 无法安装新的工作负载、组件或语言。  | `--layout`  | 如果要从部分布局进行安装，并且选择之前布局中不可用的工作负载、组件或语言，请确保可连接到 Internet。 |

### <a name="how-to-get-support-for-your-offline-installer"></a>如何获取关于脱机安装程序的支持
如果脱机安装遇到问题，请告知我们。 告知我们的最好方式是使用[报告问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具。 使用此工具时，可发送我们诊断和修复问题所需的遥测数据和日志。

我们还提供其他支持选项。 有关列表，请参阅[联系我们](../ide/how-to-report-a-problem-with-visual-studio-2017.md)页。


## <a name="see-also"></a>另请参阅
* [安装 Visual Studio](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 工作负荷和组件 ID](workload-and-component-ids.md)

