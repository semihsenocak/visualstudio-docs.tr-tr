---
title: Etki alanı özelliklerinin özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain properties
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3c1bd47ce583c790fdc90a4135184b21a932f449
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690265"
---
# <a name="properties-of-domain-properties"></a>Etki Alanı Özelliklerinin Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda en son sürümünü şu yolda bulunabilir: [etki alanı özelliklerinin özellikleri](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-properties).  
  
A *domain özelliği* değer tutan bir model öğesi olan bir özelliktir. Örneğin, `Person` etki alanı sınıfı özellikleri vardır `Name` ve `BirthDate`. DSL tanımındaki etki alanı özellikleri, etki alanı sınıfı kutusuna Diyagramı'nda ve etki alanı sınıfı, DSL Gezgini altında listelenir. Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  "Özelliği" sözcüğü iki kullanımı vardır. A *domain özelliği* üzerinde bir etki alanı sınıfı tanımlayan bir özelliktir. Bunun aksine, DSL'nin birçok öğe sahip *özellikleri*, bu makalenin **özellikleri** DSL tanımı penceresinde. Örneğin, her etki alanı özelliği, bu konuda açıklanan özellikler kümesi vardır.  
  
 Çalışma zamanında, bir kullanıcı etki alanı sınıfı örneğini oluşturduğunda, etki alanı özelliklerinin değerlerini Özellikler penceresinde görülebilir ve diyagramdaki şekilleri görüntülenebilir.  
  
 Çoğu etki alanı özellikleri sıradan CLR özellikleri olarak uygulanır. Ancak, bir programlama açısından bakıldığında, etki alanı özellikleri daha zengin işlevsellik sıradan program özellikleri vardır:  
  
-   Kurallar ve bir özelliğinin durumu izleme olayları tanımlayabilirsiniz. Daha fazla bilgi için [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).  
  
-   İşlem, özel olarak tutarsız durumları önlemeye yardımcı olur. Daha fazla bilgi için [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Bir diyagram veya DSL Gezgini'nde bir etki alanı özelliğini seçtiğinizde, aşağıdaki öğeleri Özellikler penceresinde görebilirsiniz. Bu öğelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Özellik|Açıklama|Varsayılan Değer|  
|--------------|-----------------|-------------------|  
|**Açıklama**|Belge oluşturulan tasarımcının kullanıcı arabirimi (UI) için kullanılan bir açıklaması.|\<yok >|  
|**Görünen ad**|Bu etki alanı özellik için oluşturulan tasarımcıda görüntülenecek ad. Boşluk ve noktalama işaretleri, örneğin "şarkı Title" içerebilir.|\<yok >|  
|**Öğe adı sağlayıcısı**|Bunun yalnızca belirlediğiniz geçerli `Is Element Name` için `true`. Varsayılan davranışı geçersiz kılma alan sınıfının yeni bir öğe için bir ad sağlar kod yazabilirsiniz.<br /><br /> DSL projesi içinde bir kod dosyasında, türetilen bir sınıf oluşturun <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Ardından DSL Gezgini DSL kök sağ tıklatın ve eklemek dış türüne tıklayın. Sınıfın adını girin.<br /><br /> Bu etki alanı özelliği yeniden seçin ve açılan listeden sınıfın adını seçin.|\<yok >|  
|**Alıcı erişim değiştiricisi**|Etki alanı sınıfı, erişim düzeyi (`public` veya `internal`). Bu özelliği erişip hangi programda kod kapsamı denetler.|`public`|  
|**Yardım anahtar sözcüğü**|Bu alan özelliği için F1 Yardımı dizini oluşturmak için kullanılan isteğe bağlı anahtar sözcük.|\<yok >|  
|**Gözatılabilir olduğu**|Varsa `True`, bu DSL modelleri açıkken etki alanı özelliği kullanıcıya Özellikler penceresinde görüntülenir.<br /><br /> Varsa `False`, etki alanı özelliği kullanıcı Arabiriminde gizlenir.<br /><br /> Görünür ancak salt okunur etki alanı özelliği yapmak istiyorsanız, **kullanıcı Arabirimi salt okunur**.|`True`|  
|**Öğe adı:**|Varsa `True`, bu etki alanı özelliği DSL Gezgini içinde model öğesinin adı olarak görüntülenir.<br /><br /> Yeni model öğeleri bu özellik için benzersiz bir varsayılan bir değer alır. Bu değerleri nasıl oluşturulacağını denetlemek istiyorsanız, **öğe adı sağlayıcısı**.|`False`|  
|**Kullanıcı Arabirimi salt okunur**|Varsa `True`, kullanıcı arabirimini kullanarak etki alanı özelliğinin değeri değiştirilemez. Programlar tarafından hala ayarlanabilir ve Özellikler penceresinde görünür.<br /><br /> Kullanıcı etki alanı özelliği gizlemek istiyorsanız, ayarlama **olan gözatılabilir**. Programlar tarafından erişimi denetlemek istiyorsanız, **ayarlayıcı erişim değiştiricisi**.|`False`|  
|**tür**|Etki alanı özelliğin türünü (`Normal`, `Calculated`, veya `CustomStorage`). Daha fazla bilgi için [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Ad**|Bu etki alanı özelliğinin adı. Örneğin geçerli bir tanımlayıcı olmalıdır **SongTitle**.|\<yok >|  
|**Notlar**|Bu etki alanı özelliği ile ilişkili resmi olmayan notlar.|\<yok >|  
|**Ayarlayıcı erişim değiştiricisi**|Ayarlayıcının erişim değiştiricisini. Bu, hangi programda kod özelliği ayarlayabilirsiniz kapsamı denetler.|`public`|  
|**Türü**|Özellik türü. Kullanılabilir türler listesine eklemek için DSL DSL Gezgini içinde kök sağ tıklayın ve tıklayın **dış türü Ekle**.|`String`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)


