---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726249"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Bu nesne tarafından temsil edilen özelliği yedeklebilecek alanı veya değişkeni (varsa) alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parametreler
`ppObject`\
dışı Destek alanını açıklayan bir [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) nesnesi, bir yönetilen kod sınıfı özelliğini, diğer bir deyişle, Get ve/veya set erişimcisi olan bir yöntemi temsil eder. Bu tür özellikler genellikle özelliği tarafından yönetilen değeri içermesi için bir değişken gerektirir. Bu değişken, yedekleme alanı olarak bilinir. Nesne için bir yedekleme alanı yoksa, bir null değer döndürtığınızdan emin olun: bazı çağıranlar dönüş değerine dikkat ödemeyebilir ancak bunun yerine null değer döndürülüp döndürülmeyeceğini göz atalım `ppObject` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
