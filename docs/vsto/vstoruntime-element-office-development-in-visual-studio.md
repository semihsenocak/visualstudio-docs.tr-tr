---
title: "&lt;vstoRuntime &gt; öğesi (Visual Studio 'Da Office geliştirme)"
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffebff9e5cee8666d1b178fca09262ecd45c99b1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584366"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `vstoRuntime`Ad alanı öğesi, `vstav3` belirli bir Office çözümü için Office çalışma zamanının Visual Studio Araçları desteklenen bir sürümünü içerir.

## <a name="syntax"></a>Sözdizimi

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `vstoRuntime`Öğesi gereklidir ve `vstav3` ad alanında bulunur. Office çözümü, Office çalışma zamanı için Visual Studio Araçları iki sürümünü destekliyorsa, `vstoRuntime` uygulama bildiriminde iki öğe vardır.

 `vstoRuntime`Öğesi aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`release`|Gereklidir. Office çalışma zamanı için Visual Studio Araçları yayın sürümü.|
|`version`|Gereklidir. Office çalışma zamanı Visual Studio Araçları sürüm numarası.|
|`supportUrl`|İsteğe bağlı. Office çalışma zamanı Visual Studio Araçları yükleme konumuna bağlantı.|

 `vstoRuntime` öğesi yok.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `vstoRuntime` kullanılarak dağıtılan bir Office çözümünün uygulama bildiriminde bulunan öğesini göstermektedir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
