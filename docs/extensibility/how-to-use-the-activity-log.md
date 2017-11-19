---
title: "如何： 使用活动日志 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d08cd747c762d7820e4744251fb00abff22b3fdc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-the-activity-log"></a>如何： 使用活动日志
Vspackage 可以将消息写入活动日志。 此功能非常适合在零售环境中进行调试 Vspackage。  
  
> [!TIP]
>  活动日志始终开启。 Visual Studio 将保持最后一个个条目，以及具有常规配置信息的前 10 个项的一个循环缓冲区。  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>若要向活动日志写入条目  
  
1.  插入此代码中的<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法或任何其他方法，但 VSPackage 构造函数中：  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     此代码获取<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服务并将强制转换到<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>接口。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>写入到活动日志中，使用当前区域性上下文的信息项。  
  
2.  加载 VSPackage 后 （通常在调用命令或打开一个窗口），会在活动日志中写入文本。  
  
### <a name="to-examine-the-activity-log"></a>若要检查活动日志  
  
1.  活动日志的子文件夹中查找 Visual Studio 数据： *%appdata%*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  使用任何文本编辑器中打开活动日志。 下面是一个典型条目：  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>可靠编程  
 由于活动日志是一项服务，则活动日志将在 VSPackage 构造函数中不可用。  
  
 你应写入之前先获取活动日志。 不要缓存或保存活动日志供将来使用。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [故障排除的 Vspackage](../extensibility/troubleshooting-vspackages.md)   
 [VSPackage](../extensibility/internals/vspackages.md)
