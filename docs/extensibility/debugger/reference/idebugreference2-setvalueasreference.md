---
title: 'IDebugReference2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4767dbe08e716d64ea03c18a1c4a6f7d6690a7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720301"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Başka bir başvurudan başvurunun değerini ayarlar. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametreler
`rgpArgs`\
'ndaki Başvuru değerinin nasıl ayarlanacağını belirlemekte kullanılan bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesneleri dizisi.

`dwArgCount`\
'ndaki Dizideki başvuruların sayısı.

`pValue`\
'ndaki Özellik değerinin ayarlanacağı bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süre (milisaniye cinsinden). `INFINITE`Sonsuza kadar beklemek için kullanın.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
