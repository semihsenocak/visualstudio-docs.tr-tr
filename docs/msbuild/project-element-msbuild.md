---
title: Proje öğesi (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632985"
---
# <a name="project-element-msbuild"></a>Proje öğesi (MSBuild)

MSBuild proje dosyasının gerekli kök öğesi.

## <a name="syntax"></a>Syntax

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
|------------------------| - |
| `DefaultTargets` | İsteğe bağlı öznitelik.<br /><br /> Hedef belirtilmemişse, varsayılan hedef veya hedefler, yapı giriş noktası olarak kullanılır. Birden çok hedef noktalı virgül (;) Ted.<br /><br /> `DefaultTargets`Öznitelikte veya MSBuild komut satırında hiçbir varsayılan hedef belirtilmemişse, [içeri aktarma](../msbuild/import-element-msbuild.md) öğeleri değerlendirildikten sonra motor proje dosyasındaki ilk hedefi yürütür. |
| `InitialTargets` | İsteğe bağlı öznitelik.<br /><br /> Öznitelikte veya komut satırında belirtilen hedeflerden önce çalıştırılacak başlangıç hedefi veya hedefleri `DefaultTargets` . Birden çok hedef noktalı virgül ( `;` ) ile ayrılmış. Birden fazla içeri aktarılan dosya tanımlanmışsa `InitialTargets` , belirtilen tüm hedefler içeri aktarmaların karşılaştığı sırada çalıştırılır. |
| `Sdk` | İsteğe bağlı öznitelik. <br /><br /> . Proj dosyasına eklenen örtük Içeri aktarma deyimleri oluşturmak için kullanılacak SDK adı ve isteğe bağlı sürüm. Sürüm belirtilmemişse, MSBuild varsayılan bir sürümü çözümlemeye çalışır.  Örneğin `<Project Sdk="Microsoft.NET.Sdk" />` veya `<Project Sdk="My.Custom.Sdk/1.0.0" />` olabilir. |
| `ToolsVersion` | İsteğe bağlı öznitelik.<br /><br /> Araç kümesi MSBuild 'in sürümü, $ (MSBuildBinPath) ve $ (Msbuildaraçları yolu) değerlerini belirlemede kullanır. |
| `TreatAsLocalProperty` | İsteğe bağlı öznitelik.<br /><br /> Genel olarak değerlendirilmeyecek Özellik adları. Bu öznitelik, belirli komut satırı özelliklerinin bir proje veya hedefler dosyasında ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmasını önler. Birden çok özellik noktalı virgül (;) Ted.<br /><br /> Normal olarak, genel özellikler proje veya hedefler dosyasında ayarlanan özellik değerlerini geçersiz kılar. Özellik `TreatAsLocalProperty` değerde listeleniyorsa, genel özellik değeri bu dosyada ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmaz. Daha fazla bilgi için bkz. [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Note:**  **-Property** (veya **-p**) anahtarını kullanarak bir komut isteminde genel özellikleri ayarlarsınız. Ayrıca, MSBuild görevinin özniteliğini kullanarak çok projeli bir derlemede alt projeler için genel özellikler ayarlayabilir veya değiştirebilirsiniz `Properties` . Daha fazla bilgi için bkz. [MSBuild görevi](../msbuild/msbuild-task.md). |
| `xmlns` | İsteğe bağlı öznitelik.<br /><br /> Belirtildiğinde, `xmlns` özniteliğinin değeri olmalıdır `http://schemas.microsoft.com/developer/msbuild/2003` . |

### <a name="child-elements"></a>Alt öğeleri

| Öğe | Açıklama |
| - | - |
| [Seçin:](../msbuild/choose-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> , `ItemGroup` Değerlendirilecek öğe ve/veya öğe kümesi seçmek için alt öğeleri değerlendirir `PropertyGroup` . |
| [İçeri Aktar](../msbuild/import-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Proje dosyasının başka bir proje dosyasını içeri aktarmasını sağlar. Bir projede sıfır veya daha fazla `Import` öğe olabilir. |
| [ImportGroup](../msbuild/importgroup-element.md) | İsteğe bağlı öğe.<br /><br /> `Import`İsteğe bağlı bir koşul altında gruplandırılan öğelerin bir koleksiyonunu içerir. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Ayrı öğeler için bir gruplandırma öğesi. Öğeler [Item](../msbuild/item-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla `ItemGroup` öğe olabilir. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Varsayılan olarak, projedeki tüm öğelere uygulanan meta veri değerleri olan öğe tanımları kümesini tanımlamanızı sağlar. ItemDefinitionGroup, görevi ve görevi kullanma gereksinimizin yerini alır `CreateItem` `CreateProperty` . |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> MSBuild olmayan bilgilerin MSBuild proje dosyasında kalıcı hale getirilmesi için bir yol sağlar. Bir projede sıfır veya bir `ProjectExtensions` öğe olabilir. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Ayrı özellikler için bir gruplandırma öğesi. Özellikler, [özellik](../msbuild/property-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla `PropertyGroup` öğe olabilir. |
| ['Sının](../msbuild/sdk-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> MSBuild proje SDK 'sına başvurur.  Bu öğe SDK özniteliğine alternatif olarak kullanılabilir. |
| [Hedef](../msbuild/target-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Sırayla yürütülecek MSBuild için bir görev kümesi içerir. Görevler, [görev](../msbuild/task-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla `Target` öğe olabilir. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> MSBuild 'e görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla `UsingTask` öğe olabilir. |

### <a name="parent-elements"></a>Üst öğeler

 Yok.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBUILD](../msbuild/msbuild.md)
