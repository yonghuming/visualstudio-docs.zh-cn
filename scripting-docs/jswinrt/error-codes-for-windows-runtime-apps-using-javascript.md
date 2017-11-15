---
title: "Windows 运行时应用使用 JavaScript 的错误代码 | Microsoft Docs"
ms.custom: 
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: "1"
author: erikadoyle
ms.author: edoyle
manager: jken
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>Windows 运行时应用使用 JavaScript 的错误代码
以下是在使用 JavaScript 开发 Windows 运行时应用时，由 Microsoft Visual Studio 控制台显示的错误代码。
  
错误 | 备注
----- | -------
APPHOST9601：“无法加载 *remoteURI*。 应用无法在本地上下文中加载远程 Web 内容。” | 有关 Web 上下文中允许的内容的详细信息，请参阅[上下文的功能和限制](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9602：“‘javascript:’是无效的属性值，将被忽略。 请不要在本地上下文中使用‘javascript:’URI。” | 出于安全原因，无法在本地上下文中使用‘javascript:’URI。 有关在本地上下文中允许的内容的详细信息，请参阅[上下文的功能和限制](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9603：“无法加载具有类 ID classID 的 ActiveX 插件。  应用无法加载 ActiveX 控件。” | 使用 JavaScript 的 Windows 运行时应用不支持自定义 Microsoft ActiveXcontrol。 如果需要 UI 控件，请使用标准 Web 控件、控件库，或创建自己的自定义控件。 如果需要执行自定义逻辑，请改为创建一个自定义 Windows 运行时对象。 有关 HTML、CSS 和 JavaScript 其他差异的信息，请参阅 [HTML、CSS 和 JavaScript 的功能和区别](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx)。
APPHOST9604：“无法导航到 uri，因为它使用无效的字符编码。  应用只能导航到 UTF8 编码的文件。” | 所有由 Windows 运行时访问的 HTML、JavaScript 和 CSS 都必须编码为 8 位 Unicode 转换格式 (UTF-8)。 有关 HTML、CSS 和 JavaScript 其他差异的信息，请参阅 [HTML、CSS 和 JavaScript 的功能和区别](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx)。
APPHOST9605：“无法从 sourceURI 导航到 targetURI，原因是目标 URI 位于安全性更高的区域。 无法从安全性较低的区域导航到安全性较高的区域，除非你正在从 Web 上下文 URI 导航到本地上下文 URI，并且已经使用 MSApp.addPublicLocalApplicationUri 方法注册过本地上下文 URI。” | 有关详细信息，请参阅 [MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx)。
APPHOST9606：“无法加载 uri，因为它使用 HTTP 连接，且存在 ms-https-connections-only 元元素。 仅当使用 ms-https-connections-only 元元素时才允许进行 HTTPS 连接。 请使用 HTTPS 连接，如果不需要安全连接，请删除此元元素。” | 有关详细信息，请参阅[如何请求 HTTPS 连接](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx)。
APPHOST9607：“由于此错误，应用无法在 uri 中启动 URI：failureCode。” | 缺少资源或无效文件是此错误的常见原因。
APPHOST9608：“由于此错误，应用无法导航到 about:blank 页：errorCode。” | 
APPHOST9610：“应用在准备导航到自定义错误页时发现错误：errorCode。” |
APPHOST9611：“由于此错误，应用无法导航到自定义错误页：errorCode。” |
APPHOST9613：“由于此错误，应用无法导航到 * uri*：errorCode。” | 
APPHOST9614：“某个 iframe 中的文档请求 requestedDocMode doc 模式，但系统强制 currentDocMode doc 模式。 此 iframe 将使用 currentDocMode doc 模式。” | 有关显示远程 Web 内容的详细信息，请参阅[如何链接到外部网页](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx)。
APPHOST9615：“应用无法在 uri 中下载此文件，因为它是在本地上下文以外通过编程方式调用的。” | 当 Web 上下文中的内容尝试通过编程方式下载文件时发生。
APPHOST9616：“此 URI 无法使用地理位置 API。  只能从属于程序包的 URI 或包含在清单的 ApplicationContentUris 元素中的 URI 调用地理位置 API。” | 有关 Web 上下文中允许的内容的详细信息，请参阅[上下文的功能和限制](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9617：“此 URI 无法使用剪贴板 API。  只能从属于程序包的 URI 或包含在清单的 ApplicationContentUris 元素中的 URI 调用剪贴板 API。” | 有关 Web 上下文中允许的内容的详细信息，请参阅[上下文的功能和限制](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9618：“此 URI 无法使用 window.close。  只能从使用 ms-appx URI 方案加载的打包内容中调用 window.close 方法。” | 有关 Web 上下文中允许的内容的详细信息，请参阅[上下文的功能和限制](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)。
APPHOST9619：“应用无法导航到 uri，因为 Web 上下文中的页面不能是应用的顶级文档。 请加载 iframe 中的页面。” | 无法将顶级页面导航到远程网页，但应用可以显示 [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx) 中的网页。 有关显示远程 Web 内容的详细信息，请参阅[如何链接到外部网页](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx)。
APPHOST9620：“此应用已关闭，因为它使用 HTTP 连接并且存在 ms-https-connections-only 元元素。 仅当使用 ms-https-connections-only 元元素时才允许进行 HTTPS 连接。 使用 HTTPS 连接，如果不需要安全连接，请删除此元元素。” | 有关详细信息，请参阅[如何请求 HTTPS 连接](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx)。
APPHOST9623：“由于此错误，应用无法解析 url：errorCode” | 此错误的常见原因是缺少文件。  
APPHOST9624：“应用无法使用脚本加载 url url，因为此 url 启动另一个应用。 只有直接用户交互才能启动另一个应用。” | 应用无法直接启动其他应用。 当应用实现特定合约时，可以由用户启动其他应用。 有关更多信息，请参阅[应用合约和扩展](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx)。
APPHOST9626：“已检测到对资源文件 `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png` 的直接引用。 在调试环境外部使用时，此引用将导致失败。” | 由于 `logo.scale-140.png` 的文件路径，此 PNG 文件将被视为本地化资源，从而导致无法直接引用本地化资源的错误。 如果想要将此文件用作语言资源，请参阅[使应用全球化 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx)。 否则，请尝试重命名有问题的目录。
  
## <a name="see-also"></a>另请参阅  
 [在 JavaScript 中使用 Windows 运行时](../jswinrt/using-the-windows-runtime-in-javascript.md)