---
title: "长双精度 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "10 字节长双精度"
  - "16 位 Windows"
  - "32 位 Windows"
  - "8 字节长双精度"
  - "80 位精度"
  - "80 位精度"
  - "8 字节长双精度"
  - "长双精度"
ms.assetid: bb581e20-b5c2-4079-8ee8-ac6739a37852
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 长双精度
Microsoft C\/C\+\+ 和 Microsoft Visual C\+\+ 上 16 位版本支持，`long double`80 位精度数据类型。  但是，在Win32编程中，`long double` 数据类型映射为 `double`，64 位的数据类型。  Microsoft 运行库向后兼容性仅提供算术函数的 `long double` 版本。  `long double` 原型函数与其 `double` 对等的原型是相同的，除此之外，`long` `double` 数据类型替换为 `double` 数据类型。  这些函数不应在 `long double` 生成新代码。  
  
### 双重函数及其长度的两个副本  
  
|功能|Long double<br /><br /> 副本|功能|Long double<br /><br /> 副本|  
|--------|------------------------|--------|------------------------|  
|[acos](/visual-cpp/c-runtime-library/reference/acos-acosf-acosl)|`acosl`|[frexp](/visual-cpp/c-runtime-library/reference/frexp)|`frexpl`|  
|[asin](/visual-cpp/c-runtime-library/reference/asin-asinf-asinl)|`asinl`|[\_hypot](/visual-cpp/c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl)|`_hypotl`|  
|[atan](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atanl`|[ldexp](/visual-cpp/c-runtime-library/reference/ldexp)|`ldexpl`|  
|[atan2](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atan2l`|[log](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`logl`|  
|[atof](/visual-cpp/c-runtime-library/reference/atof-atof-l-wtof-wtof-l)|`_atold`|[log10](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`log10l`|  
|[Bessel 函数：j0，j1，jn](../misc/bessel-functions-j0-j1-jn.md)|`j0l, j1l, jnl`|[\_matherr](/visual-cpp/c-runtime-library/reference/matherr)|`_matherrl`|  
|[Bessel 函数：y0，y1，yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|`y0l, y1l, ynl`|[modf](/visual-cpp/c-runtime-library/reference/modf-modff-modfl)|`modfl`|  
|[\_cabs](/visual-cpp/c-runtime-library/reference/cabs)|`_cabsl`|[pow](/visual-cpp/c-runtime-library/reference/pow-powf-powl)|`powl`|  
|[ceil](/visual-cpp/c-runtime-library/reference/ceil-ceilf-ceill)|`ceill`|[sin](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinl`|  
|[cos](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`cosl`|[sinh](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinhl`|  
|[cosh](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`coshl`|[sqrt](/visual-cpp/c-runtime-library/reference/sqrt-sqrtf-sqrtl)|`sqrtl`|  
|[exp](/visual-cpp/c-runtime-library/reference/exp-expf)|`expl`|[strtod](/visual-cpp/c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l)|`_strtold`|  
|[fabs](/visual-cpp/c-runtime-library/reference/fabs-fabsf-fabsl)|`fabsl`|[tan](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanl`|  
|[floor](/visual-cpp/c-runtime-library/reference/floor-floorf-floorl)|`floorl`|[tanh](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanhl`|  
|[fmod](/visual-cpp/c-runtime-library/reference/fmod-fmodf)|`fmodl`|||  
  
## 请参阅  
 [按类别分的运行时例程](/visual-cpp/c-runtime-library/run-time-routines-by-category)