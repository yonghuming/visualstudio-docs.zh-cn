---
title: "使用命令行参数安装 Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
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
ms.openlocfilehash: 18a3d03663ac96e0751d4a420244b835be7146bf
ms.lasthandoff: 02/22/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017-rc"></a>使用命令行参数安装 Visual Studio 2017 RC
在命令提示符下安装 Visual Studio 2017 RC 时，可以使用以下命令行参数（也称为开关）。  

## <a name="list-of-command-line-parameters"></a>命令行参数列表  
 Visual Studio 命令行参数不区分大小写。  

| **命令行命令** | **描述** |
| ----------------------- | --------------- |  
| ```modify``` | 修改已安装的产品。 |
| ```update``` | 更新已安装的产品。 |
| ```repair``` | 修复已安装的产品。 |
| ```uninstall``` | 卸载已安装的产品。 |

如果未指定任何命令，则将安装该产品。

| **命令行选项** | **描述** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | 要对其执行操作的实例的安装目录。 对于 install 命令，这是该实例的安装位置。 对于其他命令，这是以前安装的实例的安装位置。 |
| ```--productId <id>``` | 将要安装的实例的产品 ID。 如果指定了 --installPath，则此参数对于 install 命令是必需参数，对于其他命令则可忽略。 |
| ```--layout <dir>``` | 可选：指定一个目录来创建脱机安装缓存。 选择此选项也会隐式添加“--wait”选项。 |
| ```--lang <language-locale>``` *[<语言-区域设置> ...]* | 可选：安装/卸载指定语言的资源包。 |
| ```--add <workload or component ID>``` *[<工作负荷或组件 ID> ...]* | 可选：要添加的一个或多个工作负荷或组件 ID。 将安装项目的所需组件，而不是建议组件或可选组件。 可以使用“--includeRecommended”和/或“--includeOptional”全局控制附加组件。 若要更精细地控制，可以向 artifactId 追加“;includeRecommended”和/或“;includeOptional”（例如，“--add Workload1;includeRecommended”或“--add Workload2;includeOptional;includeRecommended”）。 |
| ```--remove <workload or component ID>``` *[<工作负荷或组件 ID> ...]* | 可选：要删除的一个或多个工作负荷或组件 ID。 |
| ```--all``` | 可选：是否安装产品的所有工作负荷和组件。 |
| ```--allWorkloads``` | 可选：安装所有工作负荷及其所需的组件，不安装建议组件或可选组件。 |
| ```--includeRecommended``` | 可选：包含所有已安装工作负荷的建议组件，但不包含可选组件。 可使用 --allWorkloads 或 --add 指定工作负荷。 |
| ```--includeOptional``` | 可选：包含所有已安装工作负荷的可选组件，但不包含建议组件。 可使用 --allWorkloads 或 --add 指定工作负荷。  |
| ```--quiet, -q``` | 可选：执行安装时不显示任何用户界面。 |
| ```--passive, -p``` | 可选：显示用户界面，但不请求用户进行任何交互。 |
| ```--norestart``` | 可选：如果存在，带有 --passive 或 --quiet 的命令不会自动重启计算机（如有必要）。 如果既未指定 --passive 也未指定 --quiet，则忽略此参数。  |
| ```--locale <language-locale>``` | 可选：更改安装程序用户界面的显示语言。 将保留设置。 |
| ```--nickname <name>``` | 可选：此参数定义分配给已安装产品的别名。 别名长度不能超过 10 个字符。  |
| ```--help, --?, -h, -?``` | 显示参数用法。 |

>注意：在指定多个工作负荷和组件时，必须对每个项重复 `--add` 或 `--remove` 命令行开关。

| **高级命令行选项** | **描述** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | 可选：将要安装的实例的通道 ID。 如果指定了 --installPath，则此参数对于 install 命令是必需参数，对于其他命令则可忽略。 |
| ```--channelUri <uri>``` | 可选：通道清单的 URI。 此参数可用于 install 命令；其他命令则可忽略。 |
| ```--installChannelUri <uri>``` | 可选：要用于安装的通道清单的 URI。 由 --channelUri 指定的 URI（指定 --installChannelUri 时必须指定此 URI）将用于检测更新。 如果不想更新，则必须指定不带参数的 --channelUri。 此参数可用于 install 命令；其他命令则可忽略。 |
| ```--installCatalogUri <uri>``` | 可选：要用于安装的目录清单的 URI。 如果指定此参数，通道管理器在使用安装通道清单中的 URI 之前，会先尝试从此 URI 下载目录清单。 此参数用于支持脱机安装，安装期间会使用已下载的产品目录创建布局缓存。 此参数可用于 install 命令；其他命令则可忽略。 |
| ```--in <path>``` | 可选：响应文件的 URI 或路径。  |
| ```--addProductLang <language-locale>``` | 可选：此参数定义将要安装的项目（组、工作负荷或组件）的语言。 它可以在命令行中出现多次。 对于 install 和 modify 命令，此参数可选；对于 update、repair 和 uninstall 命令，此参数可忽略。 如果不存在此参数，安装将使用计算机区域设置。 |
| ```--removeProductLang <language-locale>``` | 可选：此参数定义将要删除的项目（组、工作负荷或组件）的语言。 它可以在命令行中出现多次。 对于 install 和 modify 命令，此参数可选；对于 update、repair 和 uninstall 命令，此参数可忽略。 |
| ```--wait``` | 可选：进程将等待安装完成后才会返回退出代码。 在需要等待安装完成以处理来自该安装的返回代码的自动安装中，这非常有用。 |
| ```--productKey``` | 可选：这定义要用于已安装产品的产品密钥。 它由 25 个字母数字字符组成，格式为“xxxxx-xxxxx-xxxxx-xxxxx-xxxxx”或“xxxxxxxxxxxxxxxxxxxxxxxxx”。 |
## <a name="list-of-workload-ids-and-component-ids"></a>工作负荷 ID 和组件 ID 列表
有关按 Visual Studio 产品排序的工作负荷和组件 ID 的列表，请参阅我们的 [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids)（Visual Studio 2017 工作负荷和组件 ID）页面。

> [!WARNING]
> 如果安装程序 .exe 文件名包含数字，则 --layout 参数将失败。 若要解决此问题，必须从文件名 &mdash; 中删除数字，例如，将 *vs_community__198521760.1486960229.exe* 重命名为 ***vs_community.exe***。

## <a name="list-of-language-locales"></a>语言区域设置列表
| **语言-区域设置** | **语言** |
| ----------------------- | --------------- |  
| cs-CZ | 捷克语 |
| de-DE | 德语 |
| zh-CN | 英语 |
| es-ES | 西班牙语 |
| cs-CZ | 捷克语 |
| fr-FR | 法语 |
| it-IT | 意大利语 |
| ja-JP | 日语 |
| ko-KR | 朝鲜语 |
| pl-PL | 波兰语 |
| pt-BR | 葡萄牙语 - 巴西 |
| ru-RU | 俄语 |
| tr-TR | 土耳其语 |
| zh-CN | 中文 - 简体 |
| zh-TW | 中文 - 繁体 |



> [!IMPORTANT]
> 虽然一般情况下支持在生产环境中使用 Visual Studio 2017 RC，但安装 UI 中标记为“预览”的工作负荷和组件不支持在生产环境中使用。

## <a name="see-also"></a>另请参阅

 * [安装 Visual Studio](install-visual-studio.md)
 * [创建 Visual Studio 2017 RC 的脱机安装](create-an-offline-installation-of-visual-studio.md)
 * [报告 Visual Studio 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

