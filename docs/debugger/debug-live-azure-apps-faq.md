---
title: "适用的快照调试常见问题 |Microsoft 文档"
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c62269cacff6fc456d99219a5317de97c0a0ee0
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>有关在 Visual Studio 中调试快照的常见问题

下面是可能时，会显示调试使用快照调试器的实时 Azure 应用程序的问题的列表。

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>拍摄快照的性能成本是什么？

当快照调试器捕获你的应用程序的快照时，它是分叉应用的过程，并挂起分叉的副本。 调试快照时，针对过程的分叉副本中进行调试。 此过程仅 10 20 毫秒，但不会复制的应用程序; 完整的堆相反，它将复制仅的页表，并将页面设置为写入时拷贝。 如果某些的堆更改上的应用程序的对象，然后将复制各自相应的页。 每个快照因此产生很小的内存中开销 （大约为数百个对于大多数应用程序的千字节为单位）。 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>如果我遇到向外扩展 Azure App Service （的我的应用程序的多个实例），会发生什么情况？

当你有您的应用程序的多个实例时，snappoints 获取应用于每个单一实例。 仅与指定的条件命中第一个 snappoint 创建快照。 如果你有多个 snappoints，后续快照来自创建第一个快照的相同实例。 Logpoints 发送到应用程序日志将从每个实例发送消息时，Logpoints 发送到输出窗口将仅显示从一个实例的消息。 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>快照调试器如何加载符号？

快照调试器要求你具有匹配的符号为应用程序本地或部署到你的 Azure 应用程序服务 （嵌入的 Pdb 当前不支持）。 快照调试器将自动从你的 Azure 应用程序服务下载符号。 从 Visual Studio 2017 开始版本 15.2，将部署到 Azure App Service 还将部署应用程序的符号。

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>快照调试器的工作原理对我的应用程序的发布版本？

是-快照调试器旨在针对发布版本工作。 当 snappoint 放在函数中时，回使其成为可调试的调试版本中重新编译函数。 当停止快照调试器时，函数将返回到其发布版本。 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Logpoints 会导致生产应用程序中的负面影响？

否-几乎计算向应用添加任何日志消息。 它们不能在你的应用程序会导致任何副作用。 但是，某些本机属性可能无法访问与 logpoints。 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>如果我的服务器是在负载下，快照调试器是否起作用了？

是的调试快照可以用于在负载下的服务器。 快照调试器限制并不会捕获快照在情况下你的服务器上的可用内存低量的情况。

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>如何卸载快照调试器？

你可以通过以下步骤你 App Service 上卸载快照调试器站点扩展：

1. 关闭应用程序服务通过云资源管理器在 Visual Studio 或 Azure 门户中。
1. 导航到你的应用程序服务的 Kudu 站点 (即，yourappservice。**scm**。 azurewebsites.net) 并导航到**站点扩展**。
1. 单击的 X 上的快照调试器站点扩展，将其删除。

## <a name="see-also"></a>请参阅

[在 Visual Studio 中进行调试](../debugger/index.md)  
[调试使用快照调试器的实时 ASP.NET 应用程序](../debugger/debug-live-azure-applications.md)  
[有关快照调试疑难解答和已知问题](../debugger/debug-live-azure-apps-troubleshooting.md)
