---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62896363"
---
# <a name="addmessage"></a>AddMessage
Grafik tanılama *HUD* (baş ekran) için özel bir ileti ekler.

## <a name="syntax"></a>Söz dizimi

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametreler
 `szMessage` HUD 'ye eklenecek ileti.

## <a name="remarks"></a>Açıklamalar
 Grafik tanılama HUD, grafik tanılama altında çalışan uygulamanın sol üst köşesinde görüntülenir. Uygulama ve grafik bilgileri yakalama hakkında çalışma zamanı bilgilerini ve bu işlev çağırarak eklenen iletileri görüntüler.

 HUD 'ye bir ileti eklemek için grafik bilgilerini etkin bir şekilde yakalamanıza gerek kalmaz; Yani, bir ileti bir sınıf örneği aracılığıyla eklenebilir `VsgDbg` , ancak [Init](init.md) üye işlevi ilk çağrılmamalıdır. Mesajlar yalnızca HUD 'de görüntülenir, bunlar grafik günlük dosyasına kaydedilmez.