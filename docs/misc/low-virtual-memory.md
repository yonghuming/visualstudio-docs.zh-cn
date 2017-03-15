---
title: "虚拟内存不足 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec803b1-9d76-46bb-8f14-8c63d80112a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 虚拟内存不足
当虚拟内存低，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]停止响应，出现此消息。  然而，当你的计算机上的虚拟内存不足，则不会发生这个错误，而是当[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]正在运行的地址空间会发生。  最常见的是，在运行32位操作系统，这限制了[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]至2 GB的地址空间的机器会出现此错误。  在使用 32 位时只处理，该应用程序能解析内存 \(2^32 4 GB 位\)。  但是，在 32 位版本的计算机上，Windows 为内部用途保留了 2 GB 的进程虚拟地址空间（例如，用于计算机图形卡或其他系统驱动程序）。  因此，仅 32 位进程最多可以为其内部用途 2 GB。  用户可设置 \/3GB 开关确保窗口只保留 1 GB 自身， 3 GB 给进程。  在许多情况下，性能仅不降低受windows 的 1 GB 限制。  
  
 在运行 64 位版本的 windows 上系统，此错误极少发生，因为进程可以使用可寻址的空间所有 4 GB，并且，窗口可以用于 64 位内存地址与硬件和系统驱动程序一起使用。  但是，内存利用率可以超过3 GB甚至4 GB的时候[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]处理某些数据集。  有关更多信息，请参见 [Visual Studio：为什么没有 64 位版本？（也）](http://go.microsoft.com/fwlink/?LinkId=246307)。  
  
 当 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 缓存大量数据或运行多个大量耗用内存的进程时，通常会发生此错误。  
  
 以下情况涉及缓存大量数据，通常只需重新启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 即可解决。  
  
-   安装后首次运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   安装或卸载扩展。  
  
-   选择或自定义在工具箱。  
  
-   更改 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置。  
  
-   允许系统在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 打开时进入睡眠（休眠）模式。  
  
 以下情况需要大量活动内存。  在这些情况下，建议运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 时只打开基本组件，或在另一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 实例中运行其他进程。  
  
-   生成大型解决方案。  
  
-   使用大型 XML 文档。  
  
-   从[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的上一个版本升级解决方案。  
  
-   对解决方案重定目标。  
  
-   在编辑代码时，运行 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]。  
  
-   对多个项目运行 IntelliTrace。  
  
 如果这些措施并不能防止错误，可以增加您的可用地址空间的运行[!INCLUDE[win7](../debugger/includes/win7_md.md)]，如果您使用以下语法运行bcedit.exe的系统上：  
  
 **bcdedit \/set IncreaseUserVa 3072**  
  
 推荐将 x86 系统中的用户模式虚拟内存分配从 2GB 增加至 3GB。  如果添加 \/3GB switch 允许整个系统解决更多内存并为每种应用程序提供更大百分比的可用内存。  
  
> [!NOTE]
>  必须使用管理员特权运行的 bcdedit.exe。  如果不可以使用BitLocker的加密功能，则必须将其挂起，进行更改，重新启动系统，然后再重新启用BitLocker。  
  
 在添加对 3 GB 的虚拟内存分配，该错误可能会重复出现，因为任何单个应用程序但仍只能使用 2 GB 的虚拟内存。  如果这个错误继续出现，降低解决方案的大小，然后重新启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  可以降低解决方案方法是重构它会移除很少使用的项目或通过卸载不需要的项。  如果该错误，则会生成解决方案，请尝试生成它在命令提示。  
  
## 请参阅  
 [Resources for Troubleshooting IDE Errors](../ide/reference/resources-for-troubleshooting-integrated-development-environment-errors.md)