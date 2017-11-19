---
title: "测试区域 6： 删除 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a8949135bb7354ba0279ac1b6c2f0ba99fb1b2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-6-delete"></a>测试区域 6： 删除
此源代码管理插件测试区域介绍删除操作。  
  
 源控件删除中的操作的响应**解决方案资源管理器**。  
  
 以下是可以删除的项的列表：  
  
-   文件  
  
-   文件夹  
  
-   Project  
  
 具体取决于项目类型，可能可以选择**删除**（留在磁盘上的文件） 的项目或**删除**项目 （将删除磁盘上的文件）。 以上任一操作中删除项目或项从**解决方案资源管理器**。  
  
## <a name="expected-behavior"></a>预期的行为  
 在删除测试区域的测试用例预期的行为是：  
  
-   已删除的项不再在内可见**解决方案资源管理器**。  
  
-   已删除的项目或项的父签出，根据需要 （也许加上提示符。）  
  
-   删除签出或添加项之后，它不出现在**挂起签入**窗口。  
  
-   该项目仍存在在源代码管理存储区中，即使在删除后，必须手动清除。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|删除客户端项目|1.创建客户端项目。<br />2.将解决方案添加到源代码管理。<br />3.从解决方案中删除整个项目|常见的预期的行为。|  
|删除的空文件|1.创建客户端项目。<br />2.向项目中添加零字节文件。<br />3.将解决方案添加到源代码管理。<br />4.选择的文件，将其删除。|常见的预期的行为。|  
|使用一个文件中删除文件夹|1.创建单个项目的解决方案。<br />2.添加一个文件夹。<br />3.将一个文件添加到文件夹。<br />4.将解决方案添加到源代码管理。<br />5.签出该项目，以避免出现提示。<br />6.删除该文件夹。|常见的预期的行为。|  
|删除文件系统 Web 项目|1.创建文件系统 Web 项目 （使用浏览按钮来指定的 UNC 路径）。<br />2.将解决方案添加到源代码管理。<br />3.从解决方案中删除整个项目。<br />4.为本地的 Web 项目重复步骤 1 到 3 （执行不同的路径通过代码，但具有相同的外部接口和行为）。|常见的预期的行为。|  
|从文件系统 Web 项目中删除文件|1.创建文件系统 Web 项目。<br />2.将解决方案添加到源代码管理。<br />3.从项目中删除文件。<br />4.为本地的 Web 项目重复步骤 1 到 3 （执行不同的路径通过代码，但具有相同的外部接口和行为）。|常见的预期的行为。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件的测试指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)