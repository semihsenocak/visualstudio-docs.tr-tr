---
title: CreateItem görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 758491a068fe2c2c7318717f5481b41839c49a3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834409"
---
# <a name="createitem-task"></a>CreateItem Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğe koleksiyonlarını giriş öğeleriyle doldurur. Bu, öğelerin bir listeden diğerine kopyalanmasını sağlar.  
  
> [!NOTE]
> Bu görev kullanım dışıdır. .NET Framework 3,5 ' den başlayarak, öğe grupları [hedef](../msbuild/target-element-msbuild.md) öğelerin içine yerleştirilebilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Öznitelikler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `CreateItem` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalMetadata`|İsteğe bağlı `String` dizi parametresi.<br /><br /> Çıkış öğelerine iliştirilecek ek meta verileri belirtir.  Aşağıdaki sözdizimine sahip öğe için meta veri adını ve değerini belirtin:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Birden fazla meta veri adı/değer çifti noktalı virgülle ayrılmalıdır. Ad veya değer noktalı virgül ya da başka bir özel karakter içeriyorsa, bunun atlanmaları gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: MSBuild 'Teki özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çıkış öğesi koleksiyonundan dışlanacak öğeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md) ve [nasıl yapılır: derlemeden dosya çıkarma](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıkış öğesi koleksiyonuna dahil edilecek öğeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir.|  
|`PreserveExistingMetadata`|İsteğe bağlı `Boolean` parametre.<br /><br /> `True`Zaten yoksa, yalnızca ek meta verileri uygulayın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, öğe koleksiyonundan adlı yeni bir öğe koleksiyonu oluşturur `MySourceItemsWithMetadata` `MySourceItems` . `CreateItem`Görev, yeni öğe koleksiyonunu öğedeki öğelerle doldurur `MySourceItems` . Daha sonra `MyMetadata` , `Hello` Yeni koleksiyondaki her bir öğeye değeri olan adlı ek bir meta veri girişi ekler.  
  
 Görev yürütüldükten sonra `MySourceItemsWithMetadata` öğe koleksiyonu, `file1.resx` ve `file2.resx` için meta veri girdileriyle birlikte öğeleri içerir `MyMetadata` . `MySourceItems`Öğe koleksiyonu değiştirilmez.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 Aşağıdaki tabloda, görev yürütmeden sonra çıkış öğesinin değeri açıklanmaktadır. Öğe meta verileri, öğeden sonra parantez içinde gösterilir.  
  
|Öğe koleksiyonu|İçindekiler|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
