---
title: Ihata ayıklama Gpoınterobject::D ereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725571"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
İşaret eden nesneyi alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`dwIndex`\
'ndaki Nesnenin başlangıcından başlayan basit bir bayt kayması.

`ppObject`\
dışı İşaret edilen nesneyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi ve varsa, bu nesneyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür. Bu nesne başka bir nesneye işaret içermiyorsa E_FAIL döndürür.

## <a name="remarks"></a>Açıklamalar
 İşaret eden nesne, temel veya sınıf ya da yapı gibi daha karmaşık bir tür olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
