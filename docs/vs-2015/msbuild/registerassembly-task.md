---
title: RegisterAssembly görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71ef27b61e162fedbf0b8fcaac38d93bedbc77c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682399"
---
# <a name="registerassembly-task"></a>RegisterAssembly Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen derleme içindeki meta verileri okur ve gerekli girdileri kayıt defterine ekler ve bu da COM istemcilerinin sınıfları saydam olarak oluşturmalarına olanak tanır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu görevin davranışı, [Regasm.exe (derleme kayıt aracı)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)ile benzerdir, ancak aynı değildir.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `RegisterAssembly` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Assemblies`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> COM 'a kaydedilecek derlemeleri belirtir.|  
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> `RegisterAssembly`Görev ve [UnregisterAssembly](../msbuild/unregisterassembly-task.md) görevi arasındaki durumla ilgili bilgiler içerir. Bu, `UnregisterAssembly` görevin, görevde kaydettirilemedi bir derlemenin kaydını silmeye çalışmasını önler `RegisterAssembly` .|  
|`CreateCodeBase`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse, `true` kayıt defterinde, genel derleme önbelleğinde yüklü olmayan bir derlemenin dosya yolunu belirten bir kod temeli girişi oluşturur. Sonrasında genel derleme önbelleğine kaydettiriyor olduğunuz derlemeyi yükleyecekseniz bu seçeneği belirtmemelisiniz.|  
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Belirtilen derlemeden oluşturulacak tür kitaplığını belirtir. Oluşturulan tür kitaplığı, derleme içinde tanımlanan erişilebilir türlerin tanımlarını içerir. Tür kitaplığı yalnızca aşağıdakilerden biri geçerliyse üretilir:<br /><br /> -Bu ada sahip bir tür kitaplığı bu konumda yok.<br />-Bir tür kitaplığı var, ancak geçirilen derlemeden daha eski.<br /><br /> Tür kitaplığı geçilen derlemeden daha yeniyse, yeni bir tane oluşturulmaz, ancak derleme yine de kaydedilir.<br /><br /> Bu parametre belirtilmişse, parametresiyle aynı sayıda öğe olması gerekir, `Assemblies` Aksi takdirde görev başarısız olur. Hiçbir giriş belirtilmemişse, görev varsayılan olarak derlemenin adı olur ve öğenin uzantısını. tlb olarak değiştirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `RegisterAssembly` öğe koleksiyonu tarafından belirtilen derlemeyi kaydetmek için görevini kullanır `MyAssemblies` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
