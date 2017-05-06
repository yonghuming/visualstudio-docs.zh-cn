---
title: "IManagedAddin 接口"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IManagedAddin 接口"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# IManagedAddin 接口
  实现 IManagedAddin 接口可创建加载托管 VSTO 外接程序的组件。 此接口在 2007 Microsoft Office system 中添加。  
  
## 语法  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## 方法  
 下表列出 IManagedAddin 接口定义的方法。  
  
|名称|描述|  
|--------|--------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|在 Microsoft Office 应用程序加载托管 VSTO 外接程序时调用。|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|在 Microsoft Office 应用程序即将卸载 VSTO 托管外接程序时调用。|  
  
## 备注  
 从 2007 Microsoft Office system 开始，Microsoft Office 应用程序使用 IManagedAddin 接口来帮助加载 Office VSTO 外接程序。 你可以实现 IManagedAddin 接口来针对托管 VSTO 外接程序创建自己的 VSTO 外接程序加载程序和运行时，而不是使用 VSTO 外接程序加载程序 \(VSTOLoader.dll\) 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 有关更多信息，请参见[VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)。  
  
## 托管外接程序如何加载  
 应用程序启动时，会执行以下步骤：  
  
1.  应用程序通过在以下注册表项下查找项来发现 VSTO 外接程序：  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<应用程序名称\>*\\Addins\\  
  
     此注册表项下的每一项都是 VSTO 外接程序的唯一 ID。 通常情况下，这是 VSTO 外接程序程序集的名称。  
  
2.  应用程序在每个 VSTO 外接程序的注册表项下查找 `Manifest` 项。  
  
     托管 VSTO 外接程序可以在 HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<应用程序名称\>*\\Addins\\*\<外接程序 ID\>* 下的 `Manifest` 项中存储清单的完整路径。 清单是一个文件（通常是 XML 文件），提供用于帮助加载 VSTO 外接程序的信息。  
  
3.  如果应用程序找到 `Manifest` 项，便会尝试加载托管 VSTO 外接程序加载程序组件。 为此，应用程序会尝试创建实现 IManagedAddin 接口的 COM 对象。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 包括 VSTO 外接程序加载程序组件 \(VSTOLoader.dll\)，你也可以通过实现 IManagedAddin 接口来创建自己的组件。  
  
4.  应用程序调用 [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法，并传入 `Manifest` 项的值。  
  
5.  [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法执行加载 VSTO 外接程序所需的任务，例如为正在加载的 VSTO 外接程序配置应用程序域和安全策略。  
  
 有关 Microsoft Office 应用程序用于发现和加载托管 VSTO 外接程序的注册表项的详细信息，请参阅 [VSTO 外接程序的注册表项](../vsto/registry-entries-for-vsto-add-ins.md)。  
  
## IManagedAddin 实现指南  
 如果实现 IManagedAddin，则必须使用以下 CLSID 注册包含该实现的 DLL：  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Microsoft Office 应用程序使用此 CLSID 来创建实现 IManagedAddin 的 COM 对象。  
  
> [!CAUTION]  
>  此 CLSID 也由 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 中的 VSTOLoader.dll 使用。 因此，如果你使用 IManagedAddin 来创建自己的 VSTO 外接程序加载程序和运行时组件，则不能将组件部署到运行依赖于 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的 VSTO 外接程序的计算机上。  
  
## 请参阅  
 [非托管 API 参考（Visual Studio 中的 Office 开发）](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  