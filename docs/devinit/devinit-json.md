---
title: devinit yapılandırma dosyası
description: Devınit için bildirim dosyası .devinit.jsbelgeleri.
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
ms.openlocfilehash: b0cfb1c41d7721598bae44f950ced01d17ff494a
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005362"
---
# <a name="devinit-configuration-file"></a>devinit yapılandırma dosyası

## <a name="file-location"></a>Dosya konumu

`devinit.exe init`Komut, _.devinit.js_ dosyası aracılığıyla yönlendiriliyor. Varsayılan olarak, `devinit.exe` aşağıdaki konumlarda dosyayı arar:

- _{geçerli-dizin}\\_
- _{geçerli-dizin} \\ . devinit\\_
- _{geçerli-dizin} \\ . devcontainer\\_

_._ Dizin ve dosya adları atlanabilir.

Dosyadaki _.devinit.js_ , açıkça seçeneği aracılığıyla da belirlenebilir `--file` / `-f` .

### <a name="directories-and-relative-paths"></a>Dizinler ve göreli yollar

Yollar, devınit 'in çalıştığı konuma göre belirlenir. Bu, genellikle yürütülen geçerli çalışma dizinidir `devinit` .

## <a name="file-format"></a>Dosya Biçimi

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Özellik değerleri

| Ad         | Tür   | Gerekli | Değer                              |
|--------------|--------|----------|------------------------------------|
| **açıklamaları** | dize | No       | Dosya için açıklamalar.             |
| **çalışmaz**      | array  | Yes      | [RunTool nesnesi](#run-tool-object) |

#### <a name="run-tool-object"></a>Araç nesnesi Çalıştır

| Ad                  | Tür   | Gerekli | Değer                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **açıklamaları**          | dize | No       | Araç girişi için açıklamalar.                                                                               |
| **Aracı**              | string | Yes      | Araç adı. `devinit list`Kullanılabilir araçların listesi için komutuna bakın.                            |
| **girişinin**             | dize | No       | Araç girişi. Araca göre farklılık gösterir. Örneğin, gerekli sürüm, paket KIMLIĞI, dosya adı veya klasör.|
| **additionalOptions** | dize | No       | Araca geçirilecek ek komut satırı bağımsız değişkenleri.                                                |

## <a name="examples"></a>Örnekler

Devinit kullanma hakkında daha fazla örnek için [örnekler bölümüne](sample-readme.md)bakın.
