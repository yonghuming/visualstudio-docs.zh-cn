---
title: "安装问题疑难解答 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
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
ms.openlocfilehash: d8125873ab5a92d9af26c556cb2f953a606c28d9
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-failures"></a>排查 Visual Studio 2017 安装和升级故障

## <a name="symptoms"></a>症状
尝试安装或更新 Microsoft Visual Studio 2017 时，操作失败。

## <a name="workaround"></a>解决方法
若要解决此问题，请按照以下步骤操作。

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>第 1 步 - 检查此问题是否是已知问题
Visual Studio 安装程序存在一些已知问题，Microsoft 正在努力修复中。 请参阅[发行说明的“已知问题”部分](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#KIinstall)，确定你遇到的问题是否有解决办法。

### <a name="step-2---check-with-the-developer-community"></a>第 2 步 - 通过开发者社区获取帮助
在 [Visual Studio 开发者社区] (https://developercommunity.visualstudio.com/spaces/8/index.html) 上搜索你看到的错误消息。 社区的其他成员可能已记录下你遇到的问题的解决方案。

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>第 3 步 - 删除 Visual Studio 安装程序目录以修复升级问题
Visual Studio 安装程序引导程序是最轻型的可执行文件，用于安装 Visual Studio 安装程序的剩余部分。 删除 Visual Studio 安装程序文件，然后重新运行引导程序，可能会修复一些更新故障。 为此，请执行以下步骤：

1. 关闭 Visual Studio 安装程序。
2. 删除 Visual Studio 安装程序目录。 此目录通常位于 C:\Program Files (x86)\Microsoft Visual Studio\Installer。
3. 运行 Visual Studio 安装程序引导程序。 引导程序位于“下载”文件夹中，文件名格式为 ```vs_[Visual Studio edition]__*.exe```。 如果找不到此应用程序，可以转到 [Visual Studio 下载](https://www.visualstudio.com/downloads/)页，然后单击你的 Visual Studio 版本所对应的“下载”，便可下载引导程序。 运行此可执行文件，重置安装元数据。
4. 尝试重新安装或更新 Visual Studio。 如果安装程序仍无法安装，请立即查看下面的第 4 步。
<br/>**注意：**此步骤会重新安装 Visual Studio 安装程序文件，并重置安装元数据。 

### <a name="step-4---report-a-problem"></a>第 4 步 - 报告问题
在某些情况下（如出现与文件损坏相关的问题时），可能需要逐个调查每个问题：

1. 下载并运行 [Microsoft Visual Studio 和 .NET Framework 日志收集工具](https://www.microsoft.com/en-us/download/details.aspx?id=12493)。 此工具可收集并编译 Visual Studio、.NET Framework 和 SQL Server 安装的安装程序日志。
2. 打开 Visual Studio 安装程序，然后单击“报告问题”，打开 Visual Studio 反馈工具。
![可以使用 Tab 键定位到“提供反馈”按钮，从而打开反馈工具](media/report-a-problem.png)
3. 为问题报告命名一个标题，然后输入相关详细信息。 单击“下一步”，转到“附件”部分，然后附加生成的日志文件（此文件通常位于 %TEMP%\vslogs.zip）。
![使用 Tab 键定位到“报告新问题”按钮，然后完成所有相关步骤](media/problem-report-details.png)
4. 单击“下一步”，检查问题报告，然后单击“提交”。

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>第 5 步 - 运行 InstallCleanup.exe 清理安装文件
万不得已，可以运行 InstallCleanup.exe。 InstallCleanup.exe 是与 Visual Studio 安装程序一起打包的实用工具，可用于清理安装文件。 这并不是完全意义上的重新安装。 此实用工具删除的是 Visual Studio 2017 的缓存和实例数据。

1. 关闭 Visual Studio 安装程序。
2. 打开管理员命令提示符。 为此，请执行以下步骤：
   * 在“开始”菜单上，单击“运行”（“开始”键 + R）。
   * 键入“cmd”。
   * 右键单击“命令提示符”，然后选择“以管理员身份运行”。
3. 键入 InstallCleanup.exe 实用工具的完整路径，然后传递以下命令行开关：-f。 默认情况下，此实用工具的路径如下所示：
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. 重新运行第 3 步中所述的引导程序。
5. 尝试重新安装或更新 Visual Studio。

## <a name="how-to-troubleshoot-an-offline-installer"></a>如何解决脱机安装程序问题
下面的表格列出了通过本地布局进行安装时的已知问题和解决办法，可能会对你有所帮助。

| 问题       | 项                   | 解决方案 |
| ----------- | ---------------------- | -------- |
| 用户没有访问文件的权限。 | 权限 (ACL) | 请确保调整权限 (ACL)，以便他们在共享脱机安装前先向其他用户授予“读取”权限。 |
| 无法安装新的工作负载、组件或语言。  | `--layout`  | 如果要从部分布局进行安装，并且选择之前布局中不可用的工作负载、组件或语言，请确保可连接到 Internet。 |



