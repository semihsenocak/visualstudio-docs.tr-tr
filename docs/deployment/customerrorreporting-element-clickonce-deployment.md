---
title: '&lt;customErrorReporting &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d42bd1f7304d9f50b6334d9ac8ddd4f626605d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900377"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting &gt; öğesi (ClickOnce dağıtımı)
Bir hata oluştuğunda gösterilecek URI 'yi belirtir.

## <a name="syntax"></a>Syntax

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Açıklamalar
 Bu öğe isteğe bağlıdır. Bu olmadan, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] özel durum yığınını gösteren bir hata iletişim kutusu görüntüler. `customErrorReporting`Öğesi varsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bunun yerine parametresi tarafından belirtilen URI 'yi görüntüler `uri` . Hedef URI, dış özel durum sınıfını, iç özel durum sınıfını ve iç özel durum iletisini parametre olarak içerir.

 Uygulamanıza hata raporlama işlevi eklemek için bu öğeyi kullanın. Oluşturulan URI, hata türü hakkında bilgi içerdiğinden, Web siteniz bu bilgileri ayrıştırarak, örneğin uygun bir sorun giderme ekranı gibi görüntüleyebilir.

## <a name="example"></a>Örnek
 Aşağıdaki kod parçacığında, `customErrorReporting` ÜRETILEN URI 'nin üretebilecekleri bir ile birlikte öğesi gösterilmektedir.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)