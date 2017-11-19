---
title: "DONT_SAVE_VSGLOG_TO_TEMP |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 264f67eb9a1fc7f8af739d7eea329de05230c7a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
通过其存在定义图形日志文件是否保存到用户的临时文件目录。  
  
## <a name="syntax"></a>语法  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>值  
 预处理器符号，通过其存在确定是否的图形日志文件保存到用户的临时文件目录。 如果定义此符号，则通过定义的文件名称`VSG_DEFAULT_RUN_FILENAME`相对于当前目录的捕获的应用，或为绝对路径; 否则为的文件名称定义`VSG_DEFAULT_RUN_FILENAME`是相对于用户的临时文件目录，不能为绝对路径。  
  
## <a name="remarks"></a>备注  
 具体取决于用户的权限，图形日志文件可能不能保存在任意位置。 我们建议，想要将图形日志保存到用户的临时文件目录或另一已知良好位置，如果您不确定是否将选择的位置可写入到用户。  
  
 若要防止图形日志文件保存到临时文件目录，你必须定义`DONT_SAVE_VSGLOG_TO_TEMP`你包括之前`vsgcapture.h`。  
  
## <a name="example"></a>示例  
 此示例演示如何在主机上将图形日志文件保存到的绝对路径。  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)