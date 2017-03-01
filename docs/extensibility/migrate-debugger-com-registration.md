---
title: "迁移 64 位调试器 COM 类注册 |Microsoft 文档"
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e273f31cb1f43ff79fd9a4ade37d112351dea9b5
ms.lasthandoff: 02/22/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>迁移 64 位调试器 COM 类注册

>**注意︰**本文档是初定版，根据 Visual Studio 2017 RC 版本。

对于那些在 HKEY_CLASSES_ROOT 中的 COM 类注册 （通过使用 regasm，regsvr32，或直接写入注册表） 并且加载到 msvsmon.exe （远程调试器） 调试器扩展，现可能提供此注册到 msvsmon 而无需写入 HKEY_CLASSES_ROOT。 这会影响旧版.NET 调试器表达式计算器或配置为在 msvsmon.exe 进程中加载的调试引擎。

## <a name="msvsmon-comclass-def"></a>msvsmon comclass def

若要使用此方法，添加 msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64) 旁边的 *.msvsmon comclass def.json 文件。

下面是注册一个管理，一个示例 msvsmon comclass def 文件和一个本机类︰

文件名︰ MyCompany.MyExample.msvsmon comclass def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```

