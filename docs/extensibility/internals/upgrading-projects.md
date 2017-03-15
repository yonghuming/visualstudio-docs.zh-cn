---
title: "升级项目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "升级 Vspackage"
  - "升级应用程序策略"
  - "Vspackage，升级支持"
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 升级项目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

为项目模型的更改。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的一个版本变为明年   五月的要求项目和解决方案升级，以便在新版本上运行。  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 提供了可用于实现升级支持拥有项目的接口。  
  
## 升级方法  
 若要支持升级，项目系统实现必须定义和实现升级方法。  在确定方法，可以选择支持并行实现进程\) 备份，复制备份或两个。  
  
-   进程备份表示项目复制需要就地升级的那些文件，添加相应的文件名后缀，例如， “.old”。  
  
-   复制备份表示项目复制所有项目项为用户提供了备份位置。  在原始项目位置的相关文件然后升级。  
  
## 升级工作原理  
 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的早期版本中创建的解决方案较新版本中打开， IDE 检查解决方案文件确定它是否需要升级。  如果需要升级， **升级向导** 自动生成升级通过遍历该用户操作。  
  
 如果解决方案需要升级时，它会查询其升级方案中的每个项目工厂。  方法确定项目工厂是否支持复制备份或进程备份。  信息发送到 **升级向导**，集合该备份所需的信息并显示适用的选项给用户。  
  
### 多项目解决方案  
 如果解决方案包含多个项目，并升级有所不同，例如，当仅支持 SxS 备份和 Web 项目仅支持复制备份的 c. c\+\+ 项目，项目工厂必须满足升级方法。  
  
 解决方案查询 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>的每个项目工厂。  然后调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> 查看全局项目文件是否需要升级并确定支持的升级方法。  **升级向导** 然后调用。  
  
 在用户完成该向导后， <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 对执行实际升级的每个项目工厂。  为了便于备份， IVsProjectUpgradeViaFactory 方法用于升级详细信息处理的记录的 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 服务。  不能缓存此服务。  
  
 在更新所有相关全局文件后，每个项目工厂可以选择实例化项目。  项目实现必须支持 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 方法随后调用升级所有相关项目项。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法不提供 SVsUpgradeLogger 服务。  此服务可以通过调用 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>获取。  
  
## 最佳做法  
 请使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 服务检查是否可以在编辑之前编辑文件，并且可以在保存之前保存。  这将有助于该备份并升级实现处理项目文件在源代码管理下，没有足够的权限的文件，等等。  
  
 使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 服务在所有阶段备份过程中升级提供有关在成功或升级的故障进程。  
  
 有关支持和升级项目的更多信息，请在 vsshell2.idl 的 IVsProjectUpgrade 请参见注释。  
  
## 请参阅  
 [项目](../../extensibility/internals/projects.md)   
 [升级自定义项目](../../misc/upgrading-custom-projects.md)   
 [升级项目项](../../misc/upgrading-project-items.md)