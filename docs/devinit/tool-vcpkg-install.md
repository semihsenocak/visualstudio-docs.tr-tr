---
title: vcpkg-install
description: devinit Tool vcpkg-Install.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7c974b5747c38231ff4115aba17a8e3728672851
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005990"
---
# <a name="vcpkg-install"></a>vcpkg-install

`vcpkg-install`Araç, [vcpkg](https://github.com/microsoft/vcpkg)kullanılarak C/C++ kitaplıklarını (bağlantı noktaları olarak adlandırılır) almak için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek paket (ler). Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                       |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                        |

### <a name="input"></a>Giriş

`input`Özelliği, `name` bir `vcpkg` veya birden çok paket yüklemek için boşlukla ayrılmış adların bir listesi olmalıdır. Kullanılabilir bağlantı noktalarının listesi [vcpkg GitHub](https://github.com/microsoft/vcpkg/tree/master/ports)deposunda bulunabilir.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler doğrudan [vcpkg](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) komutuna geçirilir ve [Vcpkg GitHub deposu](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)'nda belgelenmiştir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracının varsayılan davranışı `vcpkg-install` , gerekli olduğu gibi hata ' dır `input` .

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the sdl2 port.",
            "tool": "vcpkg-install",
            "input": "sdl2",
        },
        {
            "comments": "Installs the sdl2 and sqlite3 ports.",
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```
