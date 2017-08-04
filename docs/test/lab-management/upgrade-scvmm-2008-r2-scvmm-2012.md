---
title: "将 SCVMM 2008 R2 升级到 SCVMM 2012 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.assetid: 5be92444-c701-43c7-8b2a-77df8e02bc27
caps.latest.revision: 56
ms.author: douge
manager: douge
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: b7874e87ea81bf6b0818b4b9eefba0f86bd2a2e2
ms.contentlocale: zh-cn
ms.lasthandoff: 06/02/2017

---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>将 SCVMM 2008 R2 升级到 SCVMM 2012

Team Foundation Server 的实验室管理工具版支持 SCVMM 2008 R2 和 SCVMM 2012。 如果要将 Team Foundation Server 2013 升级到 Team Foundation Server 2015，并计划将 SCVMM 2008 R2 升级到 SCVMM 2012，建议在完成到 Team Foundation Server 2015 的升级之后再升级到 SCVMM 2012。 本主题介绍在 Team Foundation Server 2015 上使用实验室管理工具版时如何将 SCVMM 2008 R2 升级到 SCVMM 2012。
实验室管理工具版不支持 SCVMM 2016。 

重要说明：升级 SCVMM 时，某些步骤将导致 Team Foundation Server 停机一段时间。 可在下方查看这些步骤。

## <a name="upgrading-to-scvmm-2012"></a>升级到 SCVMM 2012

1. 使用 SCVMM 2012 安装程序将 SCVMM 2008 R2 Server 升级到 SCVMM 2012 Server。

1. 在您的主机和库共享上升级 SCVMM 代理。

1. 使用 SCVMM 管理控制台验证所有 SCVMM 组件是否正在运行。

1. 在 Team Foundation Server 的应用层的所有计算机上安装 SCVMM 2012 管理控制台。

1. 使用 iisreset 命令重启 Team Foundation Server Web 服务。 然后重新启动 Team Foundation Server 作业代理。

   注意：此步骤将中断 Team Foundation Server 上的服务。

1. 升级每个项目集合数据库中的数据和模板，使其与 SCVMM 兼容 
   2012.

   在 Team Foundation Server 上打开提升的命令提示符，然后输入以下命令：

   C:\\Program Files\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\*

   使用 upgradeSCVMM 命令时，Team Foundation Server 将为使用相应模板的每个团队项目在 SCVMM 服务器上新建一个模板对象。 这确保升级您的模板以与 SCVMM 2012 兼容，而且不会丢失任何数据。 但是，创建新模板时，将向模板名称追加团队项目名称。

   注意：  
   如果新的模板名称大于 64 个字符，则将导致 SCVMM 失败。 若要解决此错误，您必须为模板指定一个较短的名称。 如果运行此命令时遇到任何其他错误或警告，请参见下一部分解决这些错误。 如果您未遇到任何错误或警告，则您的升级将完成，并且您可开始在 SCVMM 环境中使用 Lab Management。

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>使用 upgradeSCVMM 命令时解决错误和警告

使用 upgradeSCVMM 命令后，必须先解决收到的所有错误或警告，然后重新运行命令，这样才能开始使用实验室管理工具版。 使用 upgradeSCVMM 命令将生成一个日志文件，其中包含出现的所有错误和警告的相关信息。 运行 upgradeSCVMM 命令时将显示此日志文件的位置。

**SCVMM 失败：**如果遇到与 SCVMM 失败相关的错误，请使用 SCVMM 作业历史记录获取有关该错误的详细信息。 解决 SCVMM 中的错误后，重新运行 upgradeSCVMM 命令。

## <a name="see-also"></a>另请参阅

* [更改现有的实验室管理工具版配置](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)

