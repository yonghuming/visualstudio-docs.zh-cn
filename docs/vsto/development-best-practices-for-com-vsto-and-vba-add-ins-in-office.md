---
title: "用于 COM、 VSTO 和 VBA 办公室中的外接程序的开发最佳做法 |Microsoft 文档"
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: 
helpviewer_keywords: 
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2158
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 55b3a2cbaf98eeacb78f55bea23d638cd4a1ab6d
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="development-best-practices-for-com-vsto-and-vba--add-ins-in-office"></a>开发适用于 Office 中的 COM、 VSTO 和 VBA 外接程序的最佳做法
  如果你正在开发 COM，for Office 的 VSTO 或 VBA 外接程序将按照本文中所述的开发最佳做法。   这将有助于确保：

-  你的外接程序跨不同版本和部署的 Office 的兼容性。
-  外接程序部署的用户和 IT 管理员降低了复杂性。
-  不发生意外的安装或运行时失败的外接程序。

>注意： 使用[桌面桥](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)若要准备您的 COM，VSTO 或 VBA 外接程序不支持 Windows 应用商店。 无法在 Windows 应用商店或 Office 应用商店中分发 COM、 VSTO 和 VBA 加载项。 
  
## <a name="do-not-check-for-office-during-installation"></a>不检查 Office 安装期间  
 我们不建议具有外接程序中检测是否在外接程序安装过程中已安装 Office。 如果未安装 Office，你可以安装外接程序和用户将能够访问它之后安装 Office。 
  
## <a name="use-embedded-interop-types-nopia"></a>使用嵌入互操作类型 (NoPIA)  
如果你的解决方案使用.NET 4.0 或更高版本，使用嵌入互操作类型 (NoPIA) 而不是具体取决于 Office 主互操作程序集 (PIA) 可再发行组件。 使用类型嵌入减少了你的解决方案的安装大小，并确保以后的兼容性。 Office 2010 是 Office 附带 PIA 可再发行组件的最后一个版本。 有关详细信息，请参阅[演练： 嵌入 Microsoft Office 程序集中的类型信息](https://msdn.microsoft.com/en-us/library/ee317478.aspx)和[类型等效性和嵌入的互操作类型](https://docs.microsoft.com/en-us/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)。 

如果你的解决方案使用.NET 的早期版本，我们建议你更新你的解决方案使用.NET 4.0 或更高版本。 使用.NET 4.0 或更高版本可减少在较新版本的 Windows 上的运行时必备组件。
  
## <a name="avoid-depending-on-specific-office-versions"></a>避免具体取决于特定的 Office 版本  
如果你的解决方案使用选项仅适用于较新版本的 Office 的功能，请验证在运行时 （例如，使用异常处理或通过检查的版本） 的功能存在 （如果可能，在功能级别）。 验证最小版本中，而不是特定版本，如在对象模型中，使用受支持的 Api [Application.Version 属性](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx)。 我们不建议你依赖于 Office 的二进制元数据、 安装路径或注册表项的，因为这些可以安装、 环境和版本之间发生更改。

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>启用 32 位和 64 位 Office 使用   
默认的 build 目标应支持 32 位 (x86) 和 64 位 (x64)，除非你的解决方案取决于它们仅适用于特定位数的库。 在采用，尤其是在大型数据环境增加 Office 的 64 位版本。 支持 32 位和 64 位简化你的用户的 Office 的 32 位和 64 位版本之间的转换。

编写 VBA 代码时，使用 64 位安全声明语句并转换为相应的变量。 此外，请确保可以通过为每个位数提供代码运行 32 位或 64 位版本的 Office 的用户之间共享文档。 有关详细信息，请参阅[64 位 Visual Basic 应用程序概述](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx)。

## <a name="support-restricted-environments"></a>支持有限的环境   
你的解决方案不需要用户帐户提升或管理员权限。 此外，该解决方案不应依赖于设置或更改：

- 当前工作目录。
- 加载 DLL 的目录。
- PATH 变量中。

## <a name="change-the-save-location-of-shared-data-and-settings"></a>更改保存共享的数据和设置的位置
如果解决方案包含外接程序和进程对办公室外部，不要使用用户的应用程序数据文件夹或注册表交换数据或外接程序和外部进程之间的设置。 相反，请考虑使用用户的临时文件夹、 文档文件夹或你的解决方案的安装目录。

## <a name="increment-the-version-number-with-each-update"></a>增加每次更新的版本号
在你的解决方案中设置的二进制文件的版本号，并递增每次更新。 这将使用户更轻松地确定版本之间的更改，评估兼容性。

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>提供最新版本的 Office 的支持声明
客户要求 Isv 可以提供其 COM、 VSTO 和 VBA 的外接程序在 Office 中运行的支持声明。 列出您使用 Office 365 ProPlus 的显式支持语句可帮助客户准备情况工具了解您的支持。 

若要提供 Office 客户端应用程序 （例如，Word 或 Excel） 的支持声明，首先验证你的外接程序运行在当前的 Office 版本中，以及然后提交如果外接程序中断的未来版本中提供更新。 不需要 Microsoft 发布了新的生成或对 Office 的更新时，请测试你的外接程序。 Microsoft 很少更改 Office 中的 COM、 VSTO 和 VBA 扩展性平台，这些更改将妥善记录这些异常。

>重要说明： Microsoft 要维护对准备情况报表和 ISV 联系人信息的加载项受支持的列表。 若要获取外接程序列出，请参阅[https://aka.ms/readyforwindows](https://aka.ms/readyforwindows)。

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>使用进程监视器来帮助调试安装或加载问题
如果外接程序在安装或负载过程具有兼容性问题，它们可能与使用文件或注册表访问问题相关。 使用[进程监视器](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon)或类似的调试工具日志，并比较针对某个工作环境，以帮助确定此问题的行为。 
