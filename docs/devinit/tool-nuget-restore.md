---
title: NuGet-geri yükleme
description: devinit aracı NuGet-restore.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 446498f77d7f9a26c9876f6a163d819a97df1ff9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810921"
---
# <a name="nuget-restore"></a>NuGet-geri yükleme

`nuget-restore`Araç geri yükleme bağımlılıkları ve proje dosyasında belirtilen projeye özgü araçlar. NuGet geri yükleme hakkında daha fazla bilgi için [buraya](https://docs.microsoft.com/nuget/reference/cli-reference/cli-ref-restore)tıklayın.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                |
| [**girişinin**](#input)                              | dize | No       | Geri yüklenecek proje/çözüm dosyasının yolu. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                     |

### <a name="input"></a>Giriş

Geri yüklenecek proje/çözüm dosyasının yolu.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler, NuGet restore komutuna olduğu gibi geçirilir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `nuget-restore` geçerli dizinde ' NuGet restore ' öğesini çalıştıralım.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores NuGet pacakges.",
    "run": [
        {
            "tool": "nuget-restore",
            "comments": "Restores the dependencies and tools of a project using nuget restore.",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```