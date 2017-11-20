---
title: "如何： 为 ClickOnce 部署错误设置自定义日志文件位置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4a8ed7ebbd3fc2fc35e9145509ebf335652c4bbd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>如何：为 ClickOnce 部署错误设置一个自定义日志文件位置
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]维护激活的所有部署的日志文件。 这些日志记录的安装和初始化相关的任何错误[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 默认情况下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]会创建每个部署激活的一个日志文件。 它在 Internet 临时文件文件夹中存储这些日志文件。 向用户显示部署的日志文件，当出现激活失败，并且用户单击**详细信息**生成的错误对话框中。  
  
 你可以为特定客户端使用注册表编辑器更改此行为 (**regedit.exe**) 若要设置自定义日志文件路径。 在这种情况下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]单个文件中记录激活成功和失败的所有部署。  
  
> [!CAUTION]
>  注册表编辑器使用不当可造成严重的问题，可能需要重新安装操作系统。 使用注册表编辑器的风险由用户自行承担。  
  
> [!NOTE]
>  你将需要截断或删除日志文件，有时以防止它变得过大。  
  
 以下过程描述如何为单个客户端设置自定义日志文件位置。  
  
### <a name="to-set-a-custom-log-file-location"></a>若要设置自定义日志文件位置  
  
1.  打开**Regedit.exe**。  
  
2.  导航到的节点`HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`。  
  
3.  将字符串值`LogFilePath`到的完整路径和文件名你首选的自定义日志的位置。  
  
     此位置必须是用户具有写入访问权限的目录中。 例如，在 Windows Vista 上，创建以下文件夹结构并设置`LogFilePath`到 C:\Users\\< 用户名\>\Documents\Logs\ClickOnce\installation.log。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)