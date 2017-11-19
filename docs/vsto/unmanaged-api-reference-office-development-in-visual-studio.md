---
title: "非托管 API 参考 （Visual Studio 中的 Office 开发） |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
ms.assetid: cdbc70b1-1f98-43dc-a619-07d805e53dce
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 34bcfaf84f5e1258410e383e4a049403e77e5950
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>非托管 API 参考（Visual Studio 中的 Office 开发）
  从 2007 Microsoft Office system 开始，Office 应用程序使用[IManagedAddin 接口](../vsto/imanagedaddin-interface.md)接口来调用的 VSTO 外接程序加载程序组件附带[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 此组件用于帮助加载托管 VSTO 外接程序。可以通过实现此接口来创建自己的 VSTO 外接程序加载程序组件。  
  
> [!NOTE]  
>  开发扩展的 Office 体验跨解决方案是否有兴趣[多个平台](https://dev.office.com/add-in-availability)？ 查看全新[Office 外接程序模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 外接程序具有内存占用较小与 VSTO 外接程序和解决方案，相比，并且你可以通过使用几乎任何 web 编程技术，例如 HTML5、 JavaScript、 CSS3 和 XML 生成它们。  
  
## <a name="in-this-section"></a>本节内容  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)  
 一种 COM 接口，可以通过实现该接口来在 Office 应用程序中加载和卸载 VSTO 托管外接程序。  
  
  