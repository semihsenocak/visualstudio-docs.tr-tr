---
title: 'Ihata ayıklama Gpoınterobject:: SetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725507"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
İşaret edilen değeri ardışık baytların bir serisinden belirler.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parametreler
`dwStart`\
'ndaki İşaret edilen nesnenin başından itibaren bayt cinsinden bir konum.

`dwCount`\
'ndaki Ayarlanacak bayt sayısı.

`pBytes`\
'ndaki Yeni değeri temsil eden bir bayt dizisi. Bu değer, belirtilen kaydırmadan başlayarak nesnesine depolanır.

`pdwBytes`\
dışı Gerçekten ayarlanan bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bu [Ihata ayıklama Gpoınterobject](../../../extensibility/debugger/reference/idebugpointerobject.md) tarafından temsil edilen işaretçi temel bir türe veya basit türlerin basit bir dizisine (yani basit bir bayt dizisiyle temsil edilebilir bir dizi) işaret ediyorsa kullanılır. Bu `IDebugPointerObject` nesne null bir başvuru olamaz (bellekte bir adrese işaret etmelidir).

## <a name="see-also"></a>Ayrıca bkz.
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
