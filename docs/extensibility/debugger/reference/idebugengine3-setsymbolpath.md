---
title: 'IDebugEngine3:: SetSymbolPath | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730668"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Hata ayıklama sembolleri için aranan yolu veya yolları ayarlar.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Parametreler

`szSymbolSearchPath`\
'ndaki Sembol arama yolunu veya yollarını içeren dize. Ayrıntılar için "açıklamalar" başlığına bakın. Null olamaz.

`szSymbolCachePath`\
'ndaki Simgelerin önbelleğe alınbildiği yerel yolu içeren dize. Null olamaz.

`Flags`\
'ndaki Kullanılmıyor; her zaman 0 olarak ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dize, `szSymbolSearchPath` sembolleri aramak için noktalı virgülle ayrılmış bir veya daha fazla yolun listesidir. Bu yollar yerel bir yol, bir UNC stili yol veya URL olabilir. Bu yollar farklı türlerin karışımı de olabilir. Yol UNC ise (örneğin, \\ \Symserver\symbols), hata ayıklama altyapısı yolun bir sembol sunucusuna olup olmadığını belirlemelidir ve bu sunucudan sembolleri yükleyip tarafından belirtilen yolda önbelleğe almasını bilmelidir `szSymbolCachePath` .

 Sembol yolu bir veya daha fazla önbellek konumu da içerebilir. Önbellekler öncelik sırasıyla, en yüksek öncelikli önbellek ve * simgelerle ayrılmış şekilde listelenir. Örneğin:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) yöntemi, simgelerin gerçek yükünü gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
