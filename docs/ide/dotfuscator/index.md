---
title: "Dotfuscator 社区版 (CE) | Microsoft Docs"
ms.date: 2017-06-22
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保护, 社区版, 混淆, .NET, 免费, Visual Studio 2017"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "了解如何使用 Visual Studio 2017 中的免费 Dotfuscator 社区版保护 .NET 应用程序。"
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
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
ms.openlocfilehash: 15dd6127493b9977732fdb891a086f931e002459
ms.contentlocale: zh-cn
ms.lasthandoff: 06/23/2017

---

# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator 社区版 (CE)

PreEmptive Protection - Dotfuscator 提供全方位的 .NET 应用程序保护，能轻松融入用户的安全软件开发生命周期。
它可以加强、保护和精简桌面、移动、服务器和嵌入式应用程序，帮助保护商业机密和其他知识产权 (IP)，减少盗版和伪造，并防止篡改和未经授权进行调试。
Dotfuscator 无需进行其他编程，甚至无需访问源代码，即可处理已编译程序集。

![](~/ide/dotfuscator/media/header.svg)

## <a name="why-protection-matters"></a>保护为什么至关重要

**保护知识产权** (IP) 非常重要。
应用程序代码所包含的设计和实现详细信息可被视为 IP。
但是，在 .NET Framework 上构建的应用程序[包含重要的元数据和高级中间代码][assemblies]，只需使用众多免费自动化工具的其中一款即可进行反向工程，非常容易。
用户可以通过中断和阻止实施反向工程，防止未经授权的 IP 泄漏，并说明该代码包含了商业机密。
Dotfuscator 可以对 .NET 程序集[进行模糊处理][obfuscation]，以阻止实施反向工程，并保持原有的应用程序行为。

**保护应用程序的完整性**也很重要。
不良分子除实施反向工程外，还可能尝试盗版应用程序、更改应用程序在运行时的行为或操作数据。
Dotfuscator 可以赋予应用程序[检测、报告和响应未经授权的使用][checks]功能，包括篡改和第三方调试。

有关 Dotfuscator 如何融入安全软件开发生命周期的详细信息，请参阅 PreEmptive Solutions 的 [SDL 应用保护页][sdl-protection]。

## <a name="about-dotfuscator-ce"></a>关于 Dotfuscator CE

Microsoft Visual Studio 2017 副本包含了 PreEmptive Protection - Dotfuscator 社区版（也被称为 Dotfuscator CE）的副本，此副本供个人免费使用。
有关如何安装 Visual Studio 2017 随附的 Dotfuscator CE 版的说明，请参阅[安装页][install]。

Dotfuscator CE 为开发人员、架构师和测试人员提供了一系列的[软件保护和强化][software-protection]服务。
Dotfuscator CE 中包含的 [.NET 模糊处理][obfuscation]和其他[应用程序保护][app-protection]功能的示例有：

* *[重命名][renaming]*标识符，增加对已编译程序集实施反向工程的难度。
* *[防篡改][tamper]*，检测篡改应用程序的执行、发送事件警报并终止被篡改会话。
* *[防调试][debug]*，检测调试器与正在运行的应用程序的附加情况、传输事件警报并终止调试会话。
* *[应用程序到期行为][shelflife]*，对“生命周期终结”日期进行编码、在到期日期后执行应用程序时传输警报，以及终止到期应用程序会话。
* *[异常跟踪][exceptions]*，监视应用程序中发生的未经处理的异常。
* [会话][sessions]和[功能][features]使用情况跟踪，确定执行了哪些应用程序、这些应用程序的版本以及使用了这些应用程序中的哪些功能。

有关这些功能的详细信息（包括这些功能如何融入应用程序保护策略），请参阅[功能页][capabilities]。

Dotfuscator CE 提供现成的基础保护。
并且为 Dotfuscator CE 的注册用户和世界领先的 [.NET 混淆器][net-obfuscator] PreEmptive Protection - Dotfuscator 专业版的用户提供更多的应用程序保护措施。
有关增强 Dotfuscator 的信息，请参阅[升级页][upgrades]。

## <a name="getting-started"></a>入门

若要开始在 Visual Studio 中使用 Dotfuscator CE，请在“快速启动” (Ctrl+Q) 搜索栏中键入 `dotfuscator`。

* 如果已经安装 Dotfuscator CE，此操作将调出“菜单”选项以启动 Dotfuscator CE 用户界面。 有关详细信息，请参阅[完整 Dotfuscator CE 用户指南的入门页][get-started]。
* 如果尚未安装 Dotfuscator CE，此操作将调出相关的安装选项。 有关详细信息，请参阅[安装页][install]。

还可以从 [preemptive.com 上的 Dotfuscator 下载页][download]中删获取**最新版本**的 Dotfuscator CE。

## <a name="full-documentation"></a>完整文档

此页面及其子页面简要概述了 Dotfuscator CE 的功能和[此工具的安装说明][install]。

请参阅 [preemptive.com 上的完整 Dotfuscator CE 用户指南][full]了解[如何开始使用 Dotfuscator CE 用户界面][get-started]等详细的使用说明。

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[software-protection]: https://www.preemptive.com/software-protection
[obfuscation]: https://www.preemptive.com/obfuscation
[app-protection]: https://www.preemptive.com/application-protection
[sdl-protection]: https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[download]: https://www.preemptive.com/products/dotfuscator/downloads

[install]: install.md
[capabilities]: capabilities.md
[upgrades]: upgrades.md

[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_features.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/index.html

