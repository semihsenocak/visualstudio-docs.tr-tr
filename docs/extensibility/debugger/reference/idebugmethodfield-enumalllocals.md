---
title: 'IDebugMethodField:: EnumAllLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727338"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Bir derleyici tarafından oluşturulan işlemler de dahil olmak üzere, yöntemin tüm yerel değişkenleri için bir Numaralandırıcı oluşturur.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
'ndaki Belirli bir kapsam veya bağlamı işaret eden, yöntemi içindeki bir hata ayıklama adresini temsil eden bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi.

`ppLocals`\
dışı Belirtilen kapsamdaki tüm Yereller listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür; Aksi takdirde, yerelleri belirten null bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür veya Yereller yoksa S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yalnızca verilen hata ayıklama adresini içeren blok içinde tanımlanan değişkenler numaralandırılır. Bu yöntem, derleyici tarafından oluşturulan tüm yerelleri içerir. Kaynak üzerinde açıkça tanımlanmış Yereller varsa, [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) metodunu çağırın.

 Bir yöntem, birden fazla kapsam bağlamı veya blok içerebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
