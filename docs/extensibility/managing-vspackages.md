---
title: "管理 VSPackages |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
ms.author: gregvanl
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
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>管理 Vspackage
在大多数情况下，您不必担心如何管理 VSPackages 迁移，因为项目和项模板注册，并自动加载包。 但是，在某些情况下您可能需要了解一下一个以便管理您的包。  
  
## <a name="using-the-experimental-instance"></a>使用的实验实例  
 若要了解有关的实验实例的详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
## <a name="registering-and-unregistering-vspackages"></a>注册和注销 Vspackage  
 若要了解如何注册和注销 Vspackage 和其他类型的扩展，请参阅[Registering and Unregistering Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="loading-a-vspackage"></a>加载 VSPackage  
 Vspackage 可以设置为在特定 CMDUICONTEXT GUID 开启时自动加载。 有关详细信息，请参阅[加载 Vspackage](../extensibility/loading-vspackages.md)。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>使用 AsyncPackage 来加载在后台的 Vspackage  
 AsyncPackage 类使 Visual Studio 中更好的 UI 响应能力的后台线程上加载的包。 有关详细信息，请参阅[如何︰ 在后台加载 Vspackage 到使用 AsyncPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>扩展的基于规则的 UI 上下文  
 基于规则的 UI 上下文允许扩展插件作者可以定义在其下 UI 上下文被激活并关联的 Vspackage 加载的精确条件。 有关详细信息，请参阅[如何︰ 使用规则基于 Visual Studio 扩展 UI 上下文](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。  
  
## <a name="diagnosing-extension-performance"></a>诊断扩展性能  
扩展可能会影响启动及解决方案负载性能。 了解如何计算 Visual Studio 扩展的影响以及如何您可以在此分析本地测试是否作为一种性能影响扩展，扩展可能会显示。 有关详细信息，请参阅[如何︰ 诊断扩展性能](how-to-diagnose-extension-performance.md)。 
  
## <a name="troubleshooting-vspackages"></a>VSPackages 迁移故障排除  
 了解用于故障排除不加载或遇到错误的 Vspackage 的技术︰[疑难解答 Vspackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage](../extensibility/internals/vspackages.md)
