---
title: Atama ProjectConfiguration görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b543af39cbcd0301da7d0d353f8f7b6fa006f7ac
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508528"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration görevi

Bu görev bir liste yapılandırma dizelerini kabul eder ve bunları belirtilen projelere atar.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tablo, görevin parametrelerini açıklar `AssignProjectConfiguration` .

|Parametre|Açıklama|
|---------------|-----------------|
|`ProjectReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> `[]` giriş parametresi.<br /><br /> Yapılandırılacak projeler.|
|`SolutionConfigurationContents`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Her proje için bir proje yapılandırması içeren bir XML dizesi içerir. Yapılandırma, adlandırılmış projelere atanır.|
|`DefaultToVcxPlatformMapping`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> *. Vcxproj* dosyaları tarafından kullanılan çoğu tür tarafından kullanılan platform adlarından gelen, noktalı virgülle ayrılmış bir eşleşme listesi içerir.<br /><br /> Örnek:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|İsteğe Bağlı<br /><br /> `string` çıkış parametresi.<br /><br /> *. Vcxproj* platform adlarından, çoğu tür tarafından kullanılan platform adlarına yapılan eşlemelerin noktalı virgülle ayrılmış bir listesini içerir.<br /><br /> Örnek:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Geçerli projenin yapılandırmasını içerir.|
|`CurrentProjectPlatform`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Geçerli projenin platformunu içerir.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|İsteğe bağlı `bool` çıkış parametresi.<br /><br /> Başvuruların proje yapılandırmasında devre dışı bırakılmış olsa bile oluşturulması gerektiğini belirten bir bayrak içerir.|
|`ShouldUnsetParentConfigurationAndPlatform`|İsteğe bağlı `bool` çıkış parametresi.<br /><br /> Üst yapılandırmanın ve platformun atlanacağını belirten bir bayrak içerir.|
|`OutputType`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Projenin çıkış türünü içerir.|
|`ResolveConfigurationPlatformUsingMappings`|İsteğe bağlı `bool` çıkış parametresi.<br /><br /> Derleme, geçirilen proje başvurularının yapılandırma ve platformunu çözümlemek için varsayılan eşlemeleri kullanması gerekip gerekmediğini belirten bir bayrak içerir.|
|`AssignedProjects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çözümlenen başvuru yollarının listesini içerir.|
|`UnassignedProjects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Önceden çözümlenmiş çıkış listesi kullanılarak çözülemeyen proje başvuru öğelerinin listesini içerir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
