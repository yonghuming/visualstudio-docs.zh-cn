---
title: "如何︰ 使用活动日志 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage 调试"
  - "Vspackage，故障排除"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何︰ 使用活动日志
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vspackage 可以将消息写入活动日志。 此功能非常适合在零售环境中进行调试 VSPackages 迁移。  
  
> [!TIP]
>  活动日志始终处于打开状态。 Visual Studio 会保留上次一百个条目具有常规配置信息的前 10 个项的一个循环缓冲区。  
  
### 若要向活动日志写入条目  
  
1.  插入这段代码 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法或任何其他方法，但 VSPackage 构造函数中︰  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     此代码获取 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 服务并将其强制转换 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 接口。<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 将信息性条目写入活动日志，以使用当前区域性的上下文。  
  
2.  加载 VSPackage 后 （通常是在调用命令或打开一个窗口），会在活动日志中写入文本。  
  
### 活动日志中检查  
  
1.  活动日志的子文件夹中查找 Visual Studio 数据︰ *%appdata%*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML...  
  
2.  使用任何文本编辑器中打开活动日志。 以下是典型条目︰  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## 可靠编程  
 由于活动日志是一项服务，则活动日志，以将 VSPackage 构造函数中不可用。  
  
 应写入之前先获取活动日志。 不要缓存或保存以备将来使用的活动日志。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [VSPackages 迁移故障排除](../extensibility/troubleshooting-vspackages.md)   
 [Vspackage](../extensibility/internals/vspackages.md)