---
title: Hata görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5dd3214c9575a34e9265c33061b024648a221c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634233"
---
# <a name="error-task"></a>Hata görevi

Bir derlemeyi durdurup değerlendirilen bir koşullu ifadeye göre bir hata kaydeder.

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini açıklar `Error` .

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe bağlı `String` parametre.<br /><br /> Hatayla ilişkilendirilecek hata kodu. |
| `File` | İsteğe bağlı `String` parametre.<br /><br /> Hatayı içeren dosyanın adı. Dosya adı sağlanmazsa, hata görevini içeren dosya kullanılacaktır. |
| `HelpKeyword` | İsteğe bağlı `String` parametre.<br /><br /> Hatayla ilişkilendirilecek Yardım anahtar sözcüğü. |
| `Text` | İsteğe bağlı `String` parametre.<br /><br /> Parametresi olarak değerlendirilirse, günlükleri MSBuild tarafından kullanılan hata metni `Condition` `true` . |

## <a name="remarks"></a>Açıklamalar

`Error`Görev, MSBuild projelerinin günlüğe hata metni vermesini ve derleme yürütmeyi durdurmasını sağlar.

`Condition`Parametresi olarak değerlendirilirse `true` , derleme durdurulur ve bir hata günlüğe kaydedilir. Bir `Condition` parametre yoksa, hata günlüğe kaydedilir ve derleme yürütmesi duraklar. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, tüm gerekli özelliklerinin ayarlandığını doğrular. Bunlar ayarlanmamışsa, proje bir hata olayı oluşturur ve görevin parametresinin değerini günlüğe kaydeder `Text` `Error` .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
