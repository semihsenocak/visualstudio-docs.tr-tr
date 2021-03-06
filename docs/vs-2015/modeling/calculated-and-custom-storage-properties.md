---
title: Hesaplanan ve özel depolama özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 372159a7405eb7a350aa55c55cf0c7e582dc98e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668368"
---
# <a name="calculated-and-custom-storage-properties"></a>Hesaplanan ve Özel Depolama Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etki alanına özgü dil (DSL) içindeki tüm etki alanı özellikleri, diyagramda ve dil gezgininizde kullanıcıya görüntülenebilir ve program kodu tarafından erişilebilir. Ancak özellikler, değerlerinin depolandığı şekilde farklılık gösterir.

## <a name="kinds-of-domain-properties"></a>Etki alanı özelliklerinin türleri
 DSL tanımında, aşağıdaki tabloda listelendiği gibi bir etki alanı özelliği **türünü** ayarlayabilirsiniz:

|Alan özelliği türü|Description|
|--------------------------|-----------------|
|**Standart** (varsayılan)|*Depoya* kaydedilen ve dosyaya serileştirilmiş bir alan özelliği.|
|**Hesaplanmış**|Depoda kaydedilmemiş ancak diğer değerlerden hesaplanan salt bir salt okunurdur.<br /><br /> Örneğin, `Person.Age` öğesinden hesaplanabilir `Person.BirthDate` .<br /><br /> Hesaplamayı gerçekleştiren kodu sağlamanız gerekir. Genellikle, diğer etki alanı özelliklerinden değeri hesaplayabilirsiniz. Ancak dış kaynakları da kullanabilirsiniz.|
|**Özel depolama**|Doğrudan depoya kaydedilmemiş, ancak hem Get hem de set olabilecek bir etki alanı özelliği.<br /><br /> Değeri alan ve ayarlamış olan yöntemleri sağlamanız gerekir.<br /><br /> Örneğin,, `Person.FullAddress` ve içinde depolanabilir `Person.StreetAddress` `Person.City` `Person.PostalCode` .<br /><br /> Ayrıca, dış kaynaklara erişebilirsiniz. Örneğin, bir veritabanından değerler almak ve ayarlamak için.<br /><br /> Kodunuz, true olduğunda depodaki değerleri ayarlamanıza memelidir `Store.InUndoRedoOrRollback` . Bkz. [işlemler ve özel ayarlayıcılar](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Hesaplanmış veya özel bir depolama özelliği için kod sağlama
 Bir etki alanı özelliğinin türünü hesaplanmış veya özel depolama olarak ayarlarsanız, erişim yöntemleri sağlamanız gerekir. Çözümünüzü oluşturduğunuzda bir hata raporu, size gerekli olanları bildirir.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Hesaplanan veya özel bir depolama özelliği tanımlamak için

1. DslDefinition. dsl ' de, diyagramda veya **DSL Gezgini**' nde etki alanı özelliğini seçin.

2. **Özellikler** penceresinde, **tür** alanını **hesaplanan** veya **özel depolama**olarak ayarlayın.

     Ayrıca **türünü** istediğiniz gibi ayarladığınızdan emin olun.

3. **Çözüm Gezgini**araç çubuğundan **Tüm Şablonları Dönüştür** ' e tıklayın.

4. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     Şu hata iletisini alıyorsunuz: "*YourClass* , Get*yourproperty*için bir tanım içermiyor."

5. Hata iletisine çift tıklayın.

     Dsl\GeneratedCode\DomainClasses.cs veya DomainRelationships.cs açılır. Vurgulanan yöntem çağrısının üzerinde, bir yorum Get*Yourproperty*() için bir uygulama sağlamanızı ister.

    > [!NOTE]
    > Bu dosya DslDefinition. dsl 'den oluşturulur. Bu dosyayı düzenlerseniz, **Tüm Şablonları Dönüştür**' e tıkladığınızda yaptığınız değişiklikler kaybedilir. Bunun yerine, gerekli yöntemi ayrı bir dosyaya ekleyin.

6. Sınıf dosyasını ayrı bir klasörde oluşturun veya açın, örneğin CustomCode \\ *YourDomainClass*. cs.

     Ad alanının oluşturulan kodla aynı olduğundan emin olun.

7. Sınıf dosyasında, etki alanı sınıfının kısmi bir uygulamasını yazın. Sınıfında, aşağıdaki örneğe benzer eksik yöntem için bir tanım yazın `Get` :

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. **Türü** **özel depolama**olarak ayarlarsanız, bir yöntemi de belirtmeniz gerekir `Set` . Örneğin:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Kodunuz, true olduğunda depodaki değerleri ayarlamanıza memelidir `Store.InUndoRedoOrRollback` . Bkz. [işlemler ve özel ayarlayıcılar](#setters).

9. Çözümü derleyin ve çalıştırın.

10. Özelliği test edin. **Geri almayı** ve **yinelemeyi**denediğinizden emin olun.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> İşlemler ve özel ayarlayıcılar
 Özel depolama özelliğinin set yönteminde bir işlem açmanız gerekmez, çünkü Yöntem genellikle etkin bir işlem içinde çağırılır.

 Ancak, Kullanıcı geri alma veya yeniden yapma işlemini çağrılırsa veya bir işlem geri alınırsa set yöntemi de çağrılabilir. <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>True olduğunda, set yönteminiz aşağıdaki gibi davranır:

- Diğer etki alanı özelliklerine değer atama gibi, depoda değişiklik yapmamalıdır. Geri alma Yöneticisi, değerlerini ayarlayacaktır.

- Ancak, veritabanı veya dosya içerikleri gibi dış kaynakları veya mağaza dışındaki nesneleri güncelleştirmelidir. Bu, depodaki değerlerle eşitlenmiş olduklarından emin olur.

  Örneğin:

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 İşlemler hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Etki alanı özelliklerinin](../modeling/properties-of-domain-properties.md) [Program kodu özelliklerinde bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md) , [etki alanına özgü bir dili tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
