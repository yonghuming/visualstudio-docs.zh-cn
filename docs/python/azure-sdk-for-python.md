---
title: Azure SDK for Python | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fddae-8e2f-4f50-90d3-8ed2cd35c7a6
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: dfc1cc163f44a12984800882d4ac880493c0ed0b
ms.lasthandoff: 03/10/2017

---

# <a name="azure-sdk-for-python"></a>Azure SDK for Python

Azure SDK for Python 使得从运行在 Windows、Mac OSX 和 Linux 上的应用程序中使用和管理 Microsoft Azure 服务更加方便。

## <a name="installation"></a>安装

从 [Python 包索引](https://pypi.python.org/pypi/azure)安装 Azure SDK。

安装**最新稳定版**（支持 Python 2.7 和 3.3 及更高版本），如下所示：

```bash
pip install azure
```

还可按照 Azure 文档中的[安装 Python 和 SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) 操作。

## <a name="documentation"></a>文档

文档可能位于 [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html)。

[Azure SDK for Python 开发人员中心](http://azure.microsoft.com/develop/python/)也有大量有用资源，其中包括许多教程，例如：

  - 使用 [Django](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)、[Flask](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-flask-app) 和 [Bottle](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-bottle-app) 创建 Web 应用。
  - [Blob 存储](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-blob-storage)
  - [表存储](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-table-storage)
  - [队列存储](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-queue-storage)
  - [DocumentDB](https://docs.microsoft.com/azure/documentdb/documentdb-python-application)
  - [服务总线队列](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
  - [服务总线主题/订阅](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
  - [服务管理](https://docs.microsoft.com/azure/cloud-services/cloud-services-python-how-to-use-service-management)

对于不使用文档的公共 API，[SDK 的 GitHub 存储库](https://github.com/Azure/azure-sdk-for-python)中的单元测试是很好的信息来源：

- [存储单元测试](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [服务总线单元测试](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [服务管理单元测试](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [资源管理单元测试](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>支持

SDK 的 Git 存储库位于 [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python)。

如果发现任何问题或有关于 SDK 用法的任何问题，请[在存储库中提出问题](https://github.com/Azure/azure-sdk-for-python/issues)。
