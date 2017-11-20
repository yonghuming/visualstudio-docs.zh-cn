---
translation.priority.ht:
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
ms.openlocfilehash: dcac05939cd7f16de3bc5b6748134b52ac4f80d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
1.  设备或服务器你想要调试的计算机 （而不是运行 Visual Studio 的计算机） 上，获取远程工具的正确版本。

    |版本|链接|说明|
    |-|-|-|
    |Visual Studio 2017 Update 4|[远程工具](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|始终下载匹配设备操作系统 （x86 或 x64） 的版本。 对于较旧的浏览器，使用这些直接链接：[远程工具 (x64)](https://go.microsoft.com/fwlink/?LinkId=746570&clcid=0x409)和[远程工具 (x86)](https://go.microsoft.com/fwlink/?LinkId=746569&clcid=0x409)。|
    |Visual Studio 2017 （较旧）|[远程工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|如果系统提示，请加入免费的 Visual Studio Dev Essentials 组，或可以使用有效的 Visual Studio 订阅登录。 如有必要，然后重新打开该链接。|
    |Visual Studio 2015 Update 3|[远程工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|如果系统提示，请加入免费的 Visual Studio Dev Essentials 组，或可以使用有效的 Visual Studio 订阅登录。 如有必要，然后重新打开该链接。|
    |Visual Studio 2015 （较旧）|[远程工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|如果系统提示，请加入免费的 Visual Studio Dev Essentials 组，或可以使用有效的 Visual Studio 订阅登录。 如有必要，然后重新打开该链接。|
    |Visual Studio 2013|[远程工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|下载 Visual Studio 2013 文档中的页|
    |Visual Studio 2012|[远程工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|下载 Visual Studio 2012 文档中的页|
  
2.  在下载页上，选择你的操作系统 (x 86、 x64 或 ARM） 匹配的工具版本和下载远程工具。
  
    > [!IMPORTANT]
    >  我们建议你安装 Visual Studio 的版本匹配的远程工具的最新版本。 不建议不匹配的版本。 此外，你必须安装具有相同的体系结构作为你要在其安装它的操作系统的远程工具。 换而言之，如果你想要调试在远程计算机运行 64 位操作系统上的 32 位应用程序，你必须在远程计算机上安装远程工具的 64 位版本。 
    >   
    >  面 3 从 ARM 切换到 x64 体系结构。 远程工具的 ARM 版本也无法供 Visual Studio 2017。 对于 Visual Studio 2015 中，找到 Visual Studio 2015 RTW 下载中的 ARM 版本。
  
3.  当完成下载可执行文件后时，转到下一部分，然后按照安装说明。

如果你尝试将远程调试器 (msvsmon.exe) 复制到远程计算机并运行它，请注意，**远程调试器配置向导**(**rdbgwiz.exe**) 仅在你下载时安装工具。 你可能需要使用向导来配置更高版本，尤其是在你要将远程调试器作为服务运行。 有关详细信息，请参阅[（可选） 配置远程调试器作为服务](../../debugger/remote-debugging.md#bkmk_configureService)。