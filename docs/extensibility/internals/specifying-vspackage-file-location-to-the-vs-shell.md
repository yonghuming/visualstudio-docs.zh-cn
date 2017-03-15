---
title: "指定到 VS Shell VSPackage 文件位置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "托管的 VSPackages，文件位置"
  - "Vspackage，管理包文件位置"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 指定到 VS Shell VSPackage 文件位置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必须能够定位程序集 DLL 加载 VSPackage。 下表中所述，你可以以各种方式找到它。  
  
|方法|描述|  
|--------|--------|  
|使用基本代码的注册表项。|基本代码密钥可用于直接 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 从任何完全限定的文件路径加载 VSPackage 程序集。 键的值应为对 DLL 的文件路径。 这是最好的方法能够 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 加载包程序集。 此方法有时称为"基本代码\/私钥安装目录技术"。 在注册过程的基本代码的值通过传递到注册属性类的实例 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> 类型。|  
|将放置到 DLL **PrivateAssemblies** 目录。|将在该程序集 **PrivateAssemblies** 子目录 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 目录。 程序集位于 **PrivateAssemblies** 将自动检测，但不显示在 **添加引用** 对话框。 之间的差异 **PrivateAssemblies** 和 **PublicAssemblies** 是程序集在 **PublicAssemblies** 中枚举 **添加引用** 对话框。 如果您选择不使用"基本代码\/私钥 installation directory"的技术，则应安装到 **PrivateAssemblies** 目录。|  
|使用具有强名称程序集和程序集注册表项。|程序集密钥可用于显式指示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 加载强名称 VSPackage 程序集。 密钥的值应为该程序集的强名称。|  
|将放置到 DLL **PublicAssemblies** 目录。|最后，该程序集还可以将放置到 **PublicAssemblies** 子目录。 程序集位于 **PublicAssemblies** 将自动检测，并且还将显示在 **添加引用** 中对话框 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。<br /><br /> 只应将 VSPackage 的程序集放在 **PublicAssemblies** 目录，如果它们包含托管旨在由其他 VSPackage 开发人员重用的组件。 程序集的大部分不满足此条件。|  
  
> [!NOTE]
>  使用具有强名称的所有依赖程序集签名的程序集。 此外应在您自己的目录或全局程序集缓存 \(GAC\) 中安装这些程序集。 这样可以防止与具有相同的基本文件名称，称为弱名称绑定的程序集冲突。