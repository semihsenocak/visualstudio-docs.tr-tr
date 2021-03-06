---
title: ResolveNativeReference görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 137ab6c54176c7c95c13c4b3e4defb3924937bc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205633"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerel başvuruları çözümler. Sınıfını uygular <xref:Microsoft.Build.Tasks.ResolveNativeReference> . Bu sınıf, doğrudan kodunuzdan kullanılması amaçlanmayan .NET Framework altyapısını destekler.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tablo, görevin parametrelerini açıklar `ResolveNativeReference` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Gerekli [dize] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) `[]` parametresi.<br /><br /> Yerel başvuruların derleme kimliklerini çözümlemek için arama yollarını alır veya ayarlar.|  
|`ContainedComComponents`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Yerel derlemenin COM bileşenlerini alır veya ayarlar.|  
|`ContainedLooseEtcFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Yerel bildirimde listelenen gevşek vs dosyalarını alır veya ayarlar.|  
|`ContainedLooseTlbFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Yerel derlemenin gevşek. tlb dosyalarını alır veya ayarlar.|  
|`ContainedPrerequisiteAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bildirimin kullanılabilmesi için mevcut olması gereken derlemeleri alır veya ayarlar.|  
|`ContainedTypeLibraries`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Yerel derlemenin tür kitaplıklarını alır veya ayarlar.|  
|`ContainingReferenceFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Başvuru dosyalarını alır veya ayarlar.|  
|`NativeReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Win32 yerel derleme başvurularını alır veya ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
