---
title: 'IDebugCoreServer3:: Createınstanceınserver | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733025"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Sunucuda hata ayıklama altyapısının bir örneğini oluşturur.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametreler
`szDll`\
'ndaki Parametresinde belirtilen CLSID 'yi uygulayan dll 'nin yolu `clsidObject` . Bu durumda `NULL` , com `CoCreateInstance` işlevi çağrılır.

`wLangId`\
'ndaki Hata ayıklama altyapısının yerel ayarı. [Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) yönteminin çağrılmaması gerekiyorsa bu 0 olabilir.

`clsidObject`\
'ndaki Oluşturulacak hata ayıklama altyapısının CLSID değeri.

`riid`\
'ndaki Sınıf nesnesinden alınacak olan belirli bir arabirimin arabirim KIMLIĞI.

`ppvObject`\
[out] `IUnknown` oluşturulan nesneden arabirim. Bu nesneyi istenen arabirime atayın veya sıralayamaz.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
