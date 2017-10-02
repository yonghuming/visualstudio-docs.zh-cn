---
title: "Dotfuscator 的功能 | Microsoft Docs"
ms.date: 2017-06-22
ms.devlang: dotnet
ms.technology:
- vs-ide-general
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保护, 社区版, 混淆, .NET, 免费, Visual Studio 2017"
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "了解 Visual Studio 2017 中包含的免费 Dotfuscator Community Edition 的功能。"
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 9193020b9031b5e1a5637fd4ec207d0449ec85ae
ms.contentlocale: zh-cn
ms.lasthandoff: 06/23/2017

---

# <a name="capabilities-of-dotfuscator"></a>Dotfuscator 的功能

本页重点介绍 Dotfuscator Community Edition (Dotfuscator CE) 的功能，并提供了可通过[升级][upgrades]获取的对高级选项的引用。

Dotfuscator 是 .NET 应用程序的*后期生成*系统。
使用 Dotfuscator CE，Visual Studio 用户可[模糊处理程序集][obfuscation]还可将[主动防御][checks]和[分析跟踪][analytics]注入应用程序 - 全部都无需 Dotfuscator 访问原始源代码。
Dotfuscator 以多种方式保护应用程序，并创建了分层保护策略。

Dotfuscator CE 支持各种 .NET 程序集和应用程序类型，包括[通用 Windows 平台 (UWP)][uwp] 和 [Xamarin][xamarin]。

## <a name="intellectual-property-protection"></a>知识产权保护

应用程序的设计、行为和实现是各种形式的知识产权 (IP)。
但是，为 .NET Framework 创建的应用程序实质上是公开透明的；[因其包含高级元数据和中间代码][assemblies]，可以非常轻松地对 .NET 程序集进行反向工程处理。

Dotfuscator CE 中包括以[重命名][renaming]形式进行的基本 [.NET 模糊处理][obfuscation]。
使用 Dotfuscator 对代码进行模糊处理可降低通过反向工程对源代码进行未经授权访问的风险，因为重要的命名信息将不再公开。
就用户而言，模糊处理还努力保护代码免受检查 - 这在将 IP 作为商业机密进行合法保护过程中非常有价值的一步。

Dotfuscator CE 具有多种[应用程序完整性保护功能](#application-integrity-protection)，从而可进一步阻止反向工程。
例如，不良参与者为了解程序逻辑，可能尝试将调试器附加到正在运行的应用程序实例。
Dotfuscator 可以将[反调试行为][debug]注入应用程序以阻止这种情况。

## <a name="application-integrity-protection"></a>应用程序完整性保护

除了保护源代码，确保按设计使用应用程序也很重要。
攻击者可能会试图劫持应用程序，以避开许可策略（即软件盗版），窃取或操纵应用程序处理的敏感数据，或者更改应用程序的行为。

Dotfuscator CE 可将[应用程序验证代码][checks]插入程序集（包括[防篡改][tamper]和[反调试][debug]措施）。
检测到无效的应用程序状态时，验证代码可[要求应用程序代码以适当方式处理该情况][check-app]。
或者，如果不想编写代码来处理应用程序的无效使用，Dotfuscator 还可以注入[遥测报告][check-telemetry]和 [响应][check-action] 行为，无需对源代码进行任何修改。

许多这些相同的方法还可用于针对评估和试用软件，强制实施[使用周期结束的最后期限][shelflife]。

## <a name="application-monitoring"></a>应用程序监视

开发应用程序时，了解用户（包括 beta 测试人员和以前版本的用户）的行为模式至关重要。
通过应用程序分析，可以跟踪应用程序的使用频率和使用方式，包括客户遇到的问题。

Dotfuscator CE 可以将 [exception-tracking][exceptions]、[session-tracking][sessions] 和 [feature-tracking][features] 代码注入应用程序。
运行时，已处理的应用程序会将分析数据传输到已配置的 [PreEmptive Analytics 终结点][endpoints]。

## <a name="see-also"></a>另请参阅

[完整 Dotfuscator CE 用户指南中的本主题][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[uwp]: https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]: https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]: upgrades.md

[obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[analytics]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_overview.html
[endpoints]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_overview.html#endpoints

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html
[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_features.html
[check-telemetry]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_checks.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html

