---
title: FindUnderPath görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c679352fb8db81379ab93e800efa9f631773c36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149735"
---
# <a name="findunderpath-task"></a>FindUnderPath Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen öğe koleksiyonundaki hangi öğelerin belirtilen klasörün içinde veya altında olan yollara sahip olduğunu belirler.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `FindUnderPath` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yolu, parametresi tarafından belirtilen yol ile karşılaştırılacak olan dosyaları belirtir `Path` .|  
|`InPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Belirtilen yolun altında bulunan öğeleri içerir.|  
|`OutOfPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Belirtilen yolda bulunmayan öğeleri içerir.|  
|`Path`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Başvuru olarak kullanılacak klasör yolunu belirtir.|  
|`UpdateToAbsolutePaths`|İsteğe bağlı `Boolean` parametre.<br /><br /> True ise, çıkış öğelerinin yolları mutlak yollar olacak şekilde güncelleştirilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `FindUnderPath` öğesinde yer alan dosyaların, `MyFiles` özelliği tarafından belirtilen yol altında var olan yollara sahip olup olmadığını anlamak için görevini kullanır `SearchPath` . Görev tamamlandıktan sonra, `FilesNotFoundInPath` öğe `File1.txt` dosyayı içerir ve `FilesFoundInPath` öğe `File2.txt` dosyayı içerir.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)
