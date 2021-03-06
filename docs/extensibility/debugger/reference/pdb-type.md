---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714099"
---
# <a name="pdb_type"></a>PDB_TYPE

Bu yapı bir PDB sembolünden alınan alan türü hakkında bilgi belirtir.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Üyeler

`ulAppDomainID`\
Simgenin geldiği uygulamanın KIMLIĞI. Bu, uygulamanın bir örneğini benzersiz bir şekilde tanımlamak için kullanılır.

`guidModule`\
Bu alanı içeren modülün GUID 'ı.

`symid`\
Bu alana karşılık gelen simgenin KIMLIĞI.

## <a name="remarks"></a>Açıklamalar

Bu yapı, [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) `dwKind` `TYPE_INFO` yapı alanı `TYPE_KIND_PDB` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmasından bir değer) olarak ayarlandığında TYPE_INFO yapısındaki birleşimin bir parçası olarak görüntülenir.

## <a name="requirements"></a>Gereksinimler

Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
