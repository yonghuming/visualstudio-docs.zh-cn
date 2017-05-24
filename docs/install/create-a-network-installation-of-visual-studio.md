---
title: "创建基于网络的 Visual Studio 安装 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: timsneath
ms.author: tims
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: c8c48a92ba4ba75e87d947364919688032842265
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="create-a-network-installation-of-visual-studio-2017"></a>创建 Visual Studio 2017 的网络安装

企业管理员通常会创建网络安装点，以供在客户端工作站上进行部署。 我们精心设计了 Visual Studio 2017，以允许你将初始安装的相关文件以及所有产品更新缓存到一个文件夹中（有时称为_创建布局_），这样即使尚未更新到最新的服务更新，客户端工作站也可以使用同一网络位置来管理其安装。

> [!NOTE]
> 如果企业使用多个 Visual Studio 版本（例如，同时使用 Visual Studio Professional 和 Visual Studio Enterprise），需要为每个版本单独创建网络安装共享。

## <a name="download-the-visual-studio-bootstrapper"></a>下载 Visual Studio 引导程序
**下载**所需的 Visual Studio 版本。 请确保单击“保存”，然后单击“打开文件夹”。

安装程序可执行文件（具体而言是引导程序文件）将是下列项之一。

|版本 | 下载|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Visual Studio 社区 | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

其他受支持的引导包括 [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)、[vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe)、[vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe)、[vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe)、[vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) 和 [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe)。

## <a name="create-an-offline-installation-folder"></a>创建脱机安装文件夹
若要创建含所有语言和所有功能的脱机安装，请使用下面示例中的命令之一。

（请确保从下载目录运行该命令。 通常情况下，在运行 Windows 10 的计算机上为：`C:\Users\<username>\Downloads`）。

- 对于 Visual Studio Enterprise，请运行：
  ```
  vs_enterprise.exe --layout c:\vs2017offline
  ```
- 对于 Visual Studio Professional，请运行：
  ```
  vs_professional.exe --layout c:\vs2017offline
  ```
- 对于 Visual Studio Community，请运行：
  ```
  vs_community.exe --layout c:\vs2017offline
  ```

## <a name="modify-the-responsejson-file"></a>修改 response.json 文件
可以通过修改 response.json 来设置用户在运行安装程序时使用的默认值。  例如，可以通过配置 `response.json` 文件来选择一组自动选定的特定工作负载。
有关详细信息，请参阅[通过响应文件自动执行 Visual Studio 安装](automated-installation-with-response-file.md)。

## <a name="copy-the-layout-to-a-network-share"></a>将布局复制到网络共享

在网络共享上托管布局，以便用户可以从其他计算机运行。
* 示例:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```
    
## <a name="customizing-the-network-layout"></a>自定义网络布局
可使用多个选项自定义网络布局。 可以创建仅包含一组特定[语言区域设置](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)、[工作负载、组件及其推荐或可选依赖项](workload-and-component-ids.md)的部分布局。 如果确定只会将一部分工作负载部署到客户端工作站，部分布局就非常有用。 用于自定义布局的常见命令行参数包括：

 - ```--add```：用于指定[工作负载或组件 ID](workload-and-component-ids.md)。  如果使用 `--add`，只会下载使用 `--add` 指定的工作负载和组件。  如果不使用 `--add`，将下载所有工作负载和组件。
 - ```--includeRecommended```：用于添加针对指定工作负载 ID 的所有推荐组件
 - ```--includeOptional```：用于添加针对指定工作负载 ID 的所有推荐和可选组件。
 - ```--lang```：用于指定[语言区域设置](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)。
 
下面的几个示例展示了如何创建自定义部分布局。

 - 若要下载仅一种语言的所有工作负载和组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - 若要下载多种语言的所有工作负载和组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - 若要下载所有语言的一个工作负载，请运行 <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
 - 若要下载三种语言的两个工作负载和一个可选组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
 - 若要下载两个工作负载及其所有推荐组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
 - 若要下载两个工作负载及其所有推荐和可选组件，请运行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```


## <a name="deploying-from-a-network-installation"></a>从网络安装点进行部署
管理员可以通过安装脚本将 Visual Studio 部署到客户端工作站上。 拥有管理员权限的用户也可以直接从共享运行安装程序，从而在自己的计算机上安装 Visual Studio。

- 用户可以通过运行以下命令进行安装： <br>```\\server\products\VS2017\vs_enterprise.exe```
- 管理员可以通过运行以下命令在无人参与模式下进行安装： <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> 如果作为批处理文件的一部分执行，`--wait` 选项可确保 `vs_enterprise.exe` 进程先等待安装完成，然后再返回退出代码。 如果企业管理员希望对已完成的安装执行其他操作（例如，[将产品密钥应用于成功的安装](automatically-apply-product-keys-when-deploying-visual-studio.md)），这就非常有用。 这样一来，必须先等待安装完成，然后才能处理相应安装的返回代码。  如果不使用 `--wait`，vs_enterprise.exe 进程会在安装完成之前就退出，并且不会返回表示安装操作状态的准确退出代码。

### <a name="error-codes"></a>错误代码
如果使用了 `--wait` 参数，`%ERRORLEVEL%` 环境变量将会设置为下列值之一，具体视操作结果而定：

  | **值** | **结果** |
  | --------- | ---------- |
  | 0 | 操作成功完成 |
  | 3010 | 操作成功完成，但安装需要重启才能使用 |
  | 其他 | 发生了故障，请查看日志，了解详细信息 |

## <a name="updating-a-network-install-layout"></a>更新网络安装布局
当有产品更新时，不妨[将网络安装布局更新](update-a-network-installation-of-visual-studio.md)为纳入更新后的包。

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>如何为旧版 Visual Studio 2017 创建布局
**注意**：http://www.visualstudio.com 上的 VS 2017 引导程序只要运行，就会下载并安装最新版 VS 2017。 如果 VS 引导程序的下载时间是今天，运行时间是自现在起的 6 个月后，那么它安装的是以后那个时候发行的 VS 2017 版本。 如果创建布局，那么通过布局安装的则是相应布局中的特定 VS 版本。 即使可能存在更高的联机版本，也只会获取布局中的 VS 版本。

如果需要为旧版 Visual Studio 2017 创建布局，可以访问 https://my.visualstudio.com，下载“固定”版本的 Visual Studio 2017 引导程序，以获取支持的版本。这样一来，就可以为相应的旧版创建网络安装布局。 

### <a name="how-to-get-support-for-your-offline-installer"></a>如何获取关于脱机安装程序的支持
如果脱机安装遇到问题，请告知我们。 告知我们的最好方式是使用[报告问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具。 使用此工具时，可发送我们诊断和修复问题所需的遥测数据和日志。

我们还提供其他支持选项。 有关列表，请参阅[联系我们](../ide/how-to-report-a-problem-with-visual-studio-2017.md)页。

## <a name="see-also"></a>另请参阅
* [安装 Visual Studio](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 工作负荷和组件 ID](workload-and-component-ids.md)

