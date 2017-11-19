---
title: "CreateExpInstance 实用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a90a5cfdc521de0716d81b07529822f69289b605
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 实用程序
重置，请使用 CreateExpInstance 实用程序来创建，或删除 Visual Studio 的实验实例。 实验实例可用于调试和测试而无需更改基础产品的 Visual Studio 扩展。  
  
## <a name="syntax"></a>语法  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>参数  
 / 创建  
 创建的实验实例。  
  
 / 重置  
 删除实验实例中，，然后创建一个新。  
  
 /Clean  
 删除的实验实例。  
  
 / VSInstance  
 包含要复制的基本的 Visual Studio 实例的目录的名称。  
  
 / RootSuffix  
 要追加到实验实例目录的名称后缀。  
  
## <a name="remarks"></a>备注  
 当你使用 Visual Studio 扩展时，你可以按 f5 键以打开默认实验实例并安装当前的扩展。 如果没有实验实例可用时，Visual Studio 将创建一个具有默认设置。  
  
 实验实例的默认位置取决于 Visual Studio 版本号。 例如，对于 Visual Studio 2015 中，位置是 %localappdata%\Microsoft\VisualStudio\14.0Exp\ 的目录位置中的所有文件被都视为该实例的一部分。 除非目录名称更改到默认位置，否则，任何其他的实验实例将不加载由 Visual Studio 中。  
  
 在打开实验实例时，visual Studio 不会访问系统注册表。 这不同于早期版本的 Visual Studio 中，用于在用户的注册表配置单元的实验版本。  
  
 CreateExpInstance 实用工具替换 vsregex 实用程序。  
  
 下面的示例将重置默认的 Visual Studio 的实验实例。  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../../extensibility/internals/vspackages.md)