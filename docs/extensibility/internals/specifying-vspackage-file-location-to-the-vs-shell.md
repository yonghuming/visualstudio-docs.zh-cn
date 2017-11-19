---
title: "指定到 VS Shell VSPackage 文件位置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b987d5e88bcbcf02bfd80ddf5c3ed0d67a149b53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>指定到 VS Shell VSPackage 文件位置
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必须能够定位程序集 DLL 以加载 VSPackage。 下表中所述，你可以以各种方式找到它。  
  
|方法|描述|  
|------------|-----------------|  
|使用基本代码注册表项。|基本代码密钥可以用于定向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]从任何完全限定的文件路径加载 VSPackage 程序集。 键的值应为对该 DLL 的文件路径。 这是最佳办法具有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载包程序集。 此方法有时称为"基本代码/私钥安装目录技术"。 在注册过程的基本代码的值通过传递到注册特性类的实例<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>类型。|  
|将放置到 DLL **PrivateAssemblies**目录。|将在该程序集**PrivateAssemblies**子目录[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]目录。 程序集位于**PrivateAssemblies**将自动检测，但不会显示在**添加引用**对话框。 之间的差异**PrivateAssemblies**和**PublicAssemblies**是程序集在**PublicAssemblies**中枚举**添加引用**对话框。 如果你选择不使用"基本代码/私钥安装目录"的技术，则应安装到**PrivateAssemblies**目录。|  
|使用具有强名称程序集和程序集注册表项。|程序集密钥可用于显式定向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载强名称 VSPackage 程序集。 键的值应为程序集的强名称。|  
|将放置到 DLL **PublicAssemblies**目录。|最后，程序集还可以将放置到**PublicAssemblies**子目录。 程序集位于**PublicAssemblies**自动检测到，并且还将显示在**添加引用**中的对话框[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。<br /><br /> VSPackage 程序集应只放在**PublicAssemblies**目录如果它们包含托管旨在由其他 VSPackage 开发人员重用的组件。 程序集的大部分不满足此条件。|  
  
> [!NOTE]
>  所有依赖的程序集使用强名称，已签名的程序集。 这些程序集也应安装在你自己的目录或全局程序集缓存 (GAC) 中。 这样可以防止冲突程序集的具有相同的基文件名称，称为弱名称绑定。