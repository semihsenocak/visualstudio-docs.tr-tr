---
title: 'IDebugSymbolProvider:: GetAddressesFromContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719438"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Bu yöntem bir belge bağlamını bir hata ayıklama adresleri dizisiyle eşler.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametreler
`pDocContext`\
'ndaki Belge bağlamı.

`fStatmentOnly`\
'ndaki TRUE ise, hata ayıklama adreslerini tek bir deyimle sınırlandırır.

`ppEnumBegAddresses`\
dışı Bu deyimle veya satırla ilişkili başlangıç hata ayıklama adresleri için bir Numaralandırıcı döndürür.

`ppEnumEndAddresses`\
dışı Bu deyimle veya satırla ilişkili bitiş hata ayıklama adresleri için bir [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) numaralandırıcısı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Belge bağlamı genellikle kaynak satır aralığını gösterir. Bu yöntem, bu satırlarla ilişkili hata ayıklama adreslerini başlatma ve sonlandırma sağlar. Bazı diller birden çok satırı kapsayan deyimlere veya birden fazla deyim içeren satırlara izin verir. Bu yöntem, hata ayıklama adreslerini tek bir deyimle sınırlamak için bir bayrak sağlar.

 Tek bir deyimin, şablonlar söz konusu olduğunda olduğu gibi birden çok hata ayıklama adresi olması mümkündür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
