---
title: 'IDiaSymbol:: findChildrenExByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c0fcba05cb21aa3d19b79ac26ca5c70ace12e6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464578"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
Simgenin belirli bir adreste geçerli olan alt öğelerini alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT findChildrenExByAddr ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `symtag`

'ndaki [SymTagEnum numaralandırmasında](../../debugger/debug-interface-access/symtagenum.md)tanımlandığı şekilde alınacak alt öğelerin sembol etiketlerini belirtir. `SymTagNull`Tüm alt öğelerin alınması için olarak ayarlayın.

 `name`

'ndaki Alınacak alt öğelerin adını belirtir. `NULL`Tüm alt öğelerin alınması için olarak ayarlayın.

 `compareFlags`

'ndaki Ad eşleştirme için uygulanacak karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.

 `address`

'ndaki Simgenin adresi.

 `ppResult`

dışı Alınan alt simgelerin listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 `S_OK`Simgenin en az bir alt öğesi bulunursa veya `S_FALSE` alt öğe bulunmazsa öğesini döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen yerel semboller, canlı Aralık bilgilerini içerir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)