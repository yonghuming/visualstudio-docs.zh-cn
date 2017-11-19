---
title: "管理 Vspackage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55ba59a5a29181dfa3cdd70427720293582a648d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managing-vspackages"></a>管理 Vspackage
在大多数情况下，你不必担心如何管理 Vspackage，因为项目和项模板注册，并自动加载包。 但是，在某些情况下，你可能需要管理包以了解更多。  
  
## <a name="using-the-experimental-instance"></a>使用实验实例  
 若要了解有关实验实例的详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
## <a name="registering-and-unregistering-vspackages"></a>注册和注销 Vspackage  
 若要了解如何注册和注销 Vspackage 和其他类型的扩展，请参阅[注册和注销 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="loading-a-vspackage"></a>加载 VSPackage  
 Vspackage 可以设置为自动上载时特定 CMDUICONTEXT GUID 已开启。 有关详细信息，请参阅[加载 Vspackage](../extensibility/loading-vspackages.md)。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>使用 AsyncPackage 加载在后台的 Vspackage  
 AsyncPackage 类，可在 Visual Studio 中的更好 UI 响应能力后台线程上加载的包。 有关详细信息，请参阅[如何： 在后台加载 vspackage 的使用 AsyncPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>扩展基于规则的 UI 上下文  
 基于规则的 UI 上下文使扩展作者能够定义在其下激活 UI 上下文和关联的 Vspackage 加载的精确条件。 有关详细信息，请参阅[How to： 用于 Visual Studio 扩展基于使用规则的 UI 上下文](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。  
  
## <a name="diagnosing-extension-performance"></a>诊断扩展性能  
扩展可能会影响启动和解决方案负载性能。 了解如何计算 Visual Studio 扩展影响，如何它可以进行分析本地测试如果扩展中可能显示为性能影响扩展。 有关详细信息，请参阅[如何： 诊断扩展性能](how-to-diagnose-extension-performance.md)。 
  
## <a name="troubleshooting-vspackages"></a>故障排除的 Vspackage  
 了解用于故障排除不会加载，或遇到错误的 Vspackage 的技术：[疑难解答 Vspackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../extensibility/internals/vspackages.md)