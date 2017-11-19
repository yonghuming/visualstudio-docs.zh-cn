---
title: "CreatePkgDef 实用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32e9c8ffa2a9ca2bba889436f37cc4f5c3d188bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 实用程序
采用 Visual Studio 扩展作为参数的.dll 文件，并创建一个.pkgdef 文件随附.dll。 .Pkgdef 文件包含否则将在安装扩展时写入到系统注册表的所有信息。  
  
> [!NOTE]
>  大部分自动包含在 Visual Studio SDK 中的项目模板创建.pkgdef 文件作为生成过程的一部分。 本文档适用于那些希望手动创建包或转换现有的包，若要使用.pkgdef 部署。  
  
## <a name="syntax"></a>语法  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>参数  
 / =`FileName`  
 必需。 设置的.pkgdef 输出文件的名称`FileName`。  
  
 /codebase  
 可选。 强制使用基本代码实用程序的注册。  
  
 /assembly  
 强制使用程序集实用程序的注册。  
  
 `AssemblyPath`  
 你想要生成.pkgdef.dll 文件的路径。  
  
## <a name="remarks"></a>备注  
 通过使用.pkgdef 文件的扩展部署将替换 Visual Studio 的早期版本的注册表要求。  
  
 .Pkgdef 文件必须安装在以下位置之一中： %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ 或 %vsinstalldir%\Common7\IDE\Extensions\\。 如果安装文件夹为 %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\，扩展将无法识别的 Visual Studio 中，但默认情况下将被禁用。 用户可以通过启用扩展**扩展和更新**。 如果安装文件夹为 %vsinstalldir%\Common7\IDE\Extensions\\，默认情况下启用扩展。  
  
> [!NOTE]
>  **扩展和更新**工具不能用于访问扩展，除非它作为 VSIX 包的一部分安装。  
  
## <a name="see-also"></a>另请参阅  
 [CreateExpInstance 实用工具](../../extensibility/internals/createexpinstance-utility.md)