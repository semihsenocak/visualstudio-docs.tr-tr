---
title: FindInList görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915265a775f572467ad1296499bdd3201adc1f8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634155"
---
# <a name="findinlist-task"></a>FindInList görevi

Belirtilen listede, eşleşen itemspec 'e sahip bir öğe bulur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda, [Findinlist görevinin](../msbuild/findinlist-task.md)parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`CaseSensitive`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Arama büyük/küçük harfe duyarlıdır; Aksi takdirde, değildir. Varsayılan değer `true` .|
|`FindLastMatch`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` , son eşleşmeyi döndürür; Aksi takdirde, ilk eşleşmeyi döndürün. Varsayılan değer `false` .|
|`ItemFound`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Listede bulunan ilk eşleşen öğe (varsa).|
|`ItemSpecToFind`|Gerekli `String` parametre.<br /><br /> Arama yapılacak itemspec.|
|`List`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> İtemspec 'in aranacağı liste.|
|`MatchFileNameOnly`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` , itemspec 'in yalnızca dosya adı bölümüyle eşleşir; Aksi takdirde, tüm itemspec ile eşleştirin. Varsayılan değer `true` .|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
