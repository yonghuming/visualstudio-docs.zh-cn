---
title: "升级项目项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "升级项目项"
  - "项目 [Visual Studio SDK], 升级项"
  - "项目项 [Visual Studio], 升级"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 升级项目项
如果添加或管理在不实现的项目系统中的项目，则可能需要参与项目升级过程。  crystal reports 是可以添加到项目系统项的示例。  
  
 通常，项目项实现若要利用到已完全实例化，并升级的项目，因为它们需要知道该项目引用都是，以及其他项目属性在其中进行升级决定。  
  
### 获取项目升级通知  
  
1.  设置 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> 标志 \(定义在 vsshell80.idl\) 在项目项实现。  这将导致项目项 VSPackage 时自动负载，当 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell 认为项目系统是在升级过程中。  
  
2.  通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> 方法建议 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 接口。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 接口会激发，在项目系统实现完成其升级操作后，新的升级的项目中创建。  根据该方案， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 接口。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> 方法之后激发。  
  
### 升级项目项文件  
  
1.  在项目项实现必须小心管理文件备份处理。  这尤其适用于并行的备份， <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法的 `fUpgradeFlag` 参数设置为 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>，文件备份了沿子文件放置被指定为 “.old”。  备份的文件大于系统时，在中升级了可以被指定为过时。  此外，在中，除非采取具体步骤防止这一点，他们可能被复盖。  
  
2.  在项目项获取项目升级的通知时， **Visual Studio 转换向导** 仍将显示。  因此，应使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 接口的方法提供升级消息传递给向导 UI。  
  
## 请参阅  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/zh-cn/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [升级自定义项目](../misc/upgrading-custom-projects.md)