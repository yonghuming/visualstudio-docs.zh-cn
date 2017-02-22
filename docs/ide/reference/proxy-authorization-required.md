---
title: "所需的代理身份验证 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 所需的代理身份验证
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当用户通过代理服务器连接到 Visual Studio Online，而代理服务器对调用进行阻止时通常会发生此错误。 Visual Studio Online 用于使用户保持登录到 IDE 的状态。  
  
## 更正此错误  
  
-   重新启动 Visual Studio。 这时会出现一个代理身份验证对话框。 在对话框中输入你的凭据。  
  
-   如果上述步骤未能解决问题，这可能是由于你的代理服务器不提示需要提供 http:\/\/go.microsoft.com 地址的凭据，而是提示需要 \*.visualStudio.com 地址的凭据。 对于这些服务器，需要将以下列表列入到允许列表，以便取消对 Visual Studio 中所有登录方案的阻止：  
  
    -   \*.windows.net  
  
    -   \*.microsoftonline.com  
  
    -   \*.visualstudio.com  
  
    -   \*.microsoft.com  
  
    -   \*.live.com  
  
-   否则，可以从允许列表中删除 http:\/\/go.microsoft.com address 地址，以便在重启 Visual Studio 时，会对 http:\/\/go.microsoft.com 地址和服务器终结点出现代理身份验证对话框。  
  
-   或  
  
-   如果你想通过代理使用默认凭证，可以执行以下操作：  
  
    1.  查找 devenv.exe.config（devenv.exe 配置文件），查找位置为：**%ProgramFiles%\\Microsoft Visual Studio 14.0\\Common7\\IDE**（或 **%ProgramFiles\(x86\)%\\Microsoft Visual Studio 14.0\\Common7\\IDE**）。  
  
    2.  在配置文件中查找 `<system.net>` 块，并添加这个代码：  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         你必须在 `proxyaddress="<http://<yourproxy:port#>` 中为你的网络插入正确的代理地址。  
  
-   或  
  
-   你也可以按[此帖子](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx)上的说明添加允许你使用代理的代码。