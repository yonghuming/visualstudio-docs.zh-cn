---
redirect_url: shell/servicing-guidelines-for-isolated-shell-applications
title: "维护准则独立 Shell 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e15d228794fb03441d42c081f11bf75b11fdd45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>维护为独立的 Shell 应用程序的准则
分发时 Visual Studio 独立 shell 应用程序，你必须能够为安装之后，你的应用程序提供软件更新。 若要执行此操作，你必须使用 Microsoft Installer (MSI) 文件安装你的应用程序。 这种安装允许由 Microsoft 进行重新分配站点提供的软件更新下载并由无需自定义干预客户使用。  
  
## <a name="servicing-requirements"></a>服务要求  
 你可以确保你的独立的 shell 安装，可以通过确保安装程序满足以下三个条件，从而允许更新。  
  
### <a name="redistribute-by-using-an-msi"></a>通过使用 MSI 重新分发  
 你必须使用 MSI 重新分发你的应用程序，因为 MSI 会保留产品标识，可以确保应用程序具有客户端计算机上的物理位置。 合并模块 （.msm 文件） 不提供此类保证和不应使用。  
  
### <a name="accounting-for-custom-actions"></a>自定义操作的记帐  
 自定义操作是在安装程序中的非标准安装指令。 自定义操作更改参数，如文件位置、 注册表设置、 用户设置或其他安装项。 自定义操作可能会在安装时处理数据。  
  
 当你在安装程序中使用自定义操作时，你必须确保每个安装时自定义操作必须具有相应的自定义操作以便撤消操作时用户卸载应用程序。 如果安装程序无法正常工作提供对应卸载自定义操作，则删除你的应用程序将保留部分安装。  
  
-   当软件更新更改这些版本或哈希值，依赖于特定版本的文件或哈希值的自定义操作将失败。 在这种情况下你的自定义操作必须手动更新这些值。 如果产品版本之间共享的文件或哈希值的版本，则会发生另一个问题。 避免此依赖关系，只要有可能。  
  
### <a name="accounting-for-shared-files"></a>算共享文件  
 共享的文件具有相同的名称，并且可以由多个产品安装到相同的位置。 在版本、 库存单位 (SKU)，或两者中可能不同这些产品和产品可以共存于给定计算机上。 但是，共享的文件创建维护服务问题的原因：  
  
-   更新共享的文件可导致应用程序兼容性问题，因为对一个应用程序的更新可能会更改使用的第二个应用程序尚未更新的文件的版本。 安装程序共享文件的产品计数对共享文件的引用。 因此，卸载产品不会影响共享的文件超出递减值已安装的实例的计数。  
  
-   快速修补工程 (QFE) 安装程序将恢复到的 QFE 安装程序提供服务的产品版本的文件的版本。 此过程可能会中断的应用程序必须传递已更新的共享的文件。