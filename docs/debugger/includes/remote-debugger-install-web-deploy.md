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
ms.openlocfilehash: 2d82fc0eb60b2680be9ed2bdb7de13313593da0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
1. 如果你想要使用 Web 部署 Visual Studio 中部署应用程序，请在服务器上安装 Web 部署的最新版本。

    若要安装 Web 部署，使用[Web 平台安装程序 (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)或获取直接从安装程序[Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)。 在应用程序选项卡中找到 Web 部署。 

2. 验证 Web 部署正在运行正确通过打开**控制面板 > 系统和安全 > 管理工具 > 服务**并确保**Web 部署代理服务**正在运行 (服务名称是在旧版本不同）。

    如果代理服务未运行，则启动它。 如果它根本不存在，请转到**控制面板 > 程序 > 卸载程序**，查找**Microsoft Web Deploy <version>** 。 选择**更改**安装，并确保你选择**将安装到本地硬盘**Web 部署组件。 完成更改安装步骤。