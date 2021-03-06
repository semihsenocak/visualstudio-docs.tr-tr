---
title: C++ statik kod analizi Mağaza uygulamaları
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native.express
ms.assetid: c5355e43-a37c-4686-a969-18e3dfc59a9c
caps.latest.revision: 15
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c20fe8bccdf48cf307dda72a085b3c2a72f1d0cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672718"
---
# <a name="analyze-c-code-quality-of-store-apps-using-visual-studio-static-code-analysis"></a>Visual Studio statik Kod analizini kullanarak C++ kod kalitesini depolama uygulamaları çözümleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Visual Studio Express sürümlerinde Kod Analizi Aracı, bir dizi yaygın sorun ve iyi programlama uygulaması ihlalleri için kodunuzu inceler. Kod Analizi, derleyici hatalarından ve uyarılarından farklıdır, ancak sizin için veya kodunuzu kullanan diğer kişiler için hala sorun oluşturabilir. Kod Analizi, kodunuzda test aracılığıyla keşfedilmesi zor olan kusurları da bulabilir. Geliştirme işleminiz sırasında kod analizi aracını düzenli aralıklarla çalıştırmak, tamamlanmış uygulamanızın kalitesini artırabilir.

> [!NOTE]
> Visual Studio Ultimate, Visual Studio Premium ve Visual Studio Professional, kod analizi araçlarının tüm işlevselliğini kullanabilirsiniz. Bkz. MSDN kitaplığındaki [kod analizi araçlarını kullanarak uygulama kalitesini analiz etme](https://msdn.microsoft.com/library/dd264897.aspx) .

## <a name="running-code-analysis"></a><a name="BKMK_Run"></a> Kod analizini çalıştırma
 Visual Studio Çözümünüzde kod analizini çalıştırmak için:

- **Build** menüsünde, **çözüm üzerinde Kod analizini Çalıştır**' ı seçin.

  Her proje oluşturduğunuzda Kod analizini otomatik olarak çalıştırmak için:

1. Çözüm Gezgini ' de proje adını seçin ve ardından **Özellikler**' i seçin.

2. Proje özelliği sayfasında, **Kod Analizi** ' ni seçin ve ardından **derlemede C/C++ Için kod analizini etkinleştir**' i seçin.

   Çözüm derlenir ve kod analizi çalışır. Sonuçlar Kod Analizi penceresinde görünür.

   ![Kod Analizi penceresi](../test/media/ca-cpp-collapsed.png "CA_CPP_Collapsed")

## <a name="analyzing-and-resolving-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Kod Analizi uyarılarını çözümleme ve çözme
 Belirli bir uyarıyı çözümlemek için, Kod Analizi penceresinde uyarının başlığını seçin. Uyarı, sorunla ilgili ayrıntılı bilgileri görüntüleyecek şekilde genişler. Mümkün olduğunda, kod analizi uyarıya yol gösteren satır numarasını ve analiz mantığını görüntüler.

 ![Genişletilmiş kod analizi uyarısı](../test/media/ca-cpp-expanded-callout.png "CA_CPP_Expanded_Callout")

 Bir uyarı genişlettiğinizde, uyarıya neden olan kod satırları Visual Studio kod Düzenleyicisi 'nde vurgulanır.

 ![Vurgulanan kaynak kodu](../test/media/ca-cpp-sourceline.png "CA_CPP_SourceLine")

 Sorunu anladıktan sonra kodunuzda çözebilirsiniz. Daha sonra uyarının Kod Analizi penceresinde göründüğünden ve düzelmenizin yeni uyarılar gerçekleştirmediğinden emin olmak için kod analizini yeniden çalıştırın.

> [!TIP]
> Kod Analizi penceresinden Kod analizini yeniden çalıştırabilirsiniz. **Çözümle** düğmesini seçin ve ardından analizin kapsamını seçin. Çözümlemeyi çözümün tamamında veya seçili bir projede yeniden çalıştırabilirsiniz.

## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Kod Analizi uyarılarını gizleme
 Kod Analizi uyarısının düzeltilmeyeceğine karar verirken zamanlar olabilir. Uyarı çözmenin, kodunuzun gerçek hayatta herhangi bir uygulamada ortaya çıkması olasılığa göre çok fazla kaynak gerektirir. Ya da uyarıda kullanılan çözümlemenin belirli bir bağlam için uygun olmadığından emin olabilirsiniz. Kod Analizi penceresinde artık görünmemek için tek tek uyarıları bastırın.

 Bir uyarıyı bastırmak için:

1. Ayrıntılı bilgiler görüntülenmiyorsa, uyarının başlığını genişletin.

2. Uyarının altındaki **Eylemler** bağlantısını seçin.

3. **Iletiyi bastırın** ve ardından **kaynak '** ı seçin.

   Bir iletinin gizlenmesi `#pragma(warning:` *WarningId* `)` , kod satırıyla ilgili uyarıyı belirten warnıngıd öğesini ekler.

## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Kod analizi sonuçlarını arama ve filtreleme
 Uyarı iletilerinin uzun listelerinde arama yapabilir ve çok projeli çözümlerde uyarıları filtreleyebilirsiniz.

 ![Kod Analizi penceresinde arama ve filtreleme](../test/media/ca-searchfilter.png "CA_SearchFilter")

## <a name="c-code-analysis-warnings"></a><a name="Warnings"></a> C++ kod analizi uyarıları
 Kod Analizi, C++ kodu için aşağıdaki uyarıları oluşturur:

|                                      Kural                                      |                                                  Description                                                  |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
|                       [C6001](../code-quality/c6001.md)                        |                                          Başlatılmamış belleği kullanma                                           |
|                       [C6011](../code-quality/c6011.md)                        |                                          Null Işaretçisinin başvurusu                                           |
|                       [C6029](../code-quality/c6029.md)                        |                                            Işaretlenmemiş değer kullanımı                                             |
|                       [C6053](../code-quality/c6053.md)                        |                                          Çağrıdan sıfır sonlandırma                                           |
|                       [C6059](../code-quality/c6059.md)                        |                                               Hatalı birleştirme                                               |
|                       [C6063](../code-quality/c6063.md)                        |                                  Biçimlendirme Işlevinde dize bağımsız değişkeni eksik                                   |
|                       [C6064](../code-quality/c6064.md)                        |                                  Biçimlendirme Işlevinde eksik tamsayı bağımsız değişkeni                                  |
|                       [C6066](../code-quality/c6066.md)                        |                                  Biçimlendirme Işlevinde eksik Işaretçi değişkeni                                  |
|                       [C6067](../code-quality/c6067.md)                        |                              Biçimlendirme Işlevinde eksik dize Işaretçisi bağımsız değişkeni                               |
|                       [C6101](../code-quality/c6101.md)                        |                                        Başlatılmamış bellek döndürülüyor                                         |
|                       [C6200](../code-quality/c6200.md)                        |                                         Dizin, arabellek üst sınırını aşıyor                                          |
|                       [C6201](../code-quality/c6201.md)                        |                                      Dizin yığın arabelleği üst sınırını aşıyor                                       |
|                       [C6270](../code-quality/c6270.md)                        |                                   Biçimlendirme Işlevinde float bağımsız değişkeni eksik                                   |
|                       [C6271](../code-quality/c6271.md)                        |                                       Biçim Işlevine fazladan bağımsız değişken                                       |
|                       [C6272](../code-quality/c6272.md)                        |                                     Biçimlendirme Işlevinde kayan olmayan bağımsız değişken                                     |
|                       [C6273](../code-quality/c6273.md)                        |                                    Biçimlendirme Işlevinde tamsayı olmayan bağımsız değişken                                     |
|                       [C6274](../code-quality/c6274.md)                        |                                   Biçimlendirme Işlevinde karakter olmayan bağımsız değişken                                   |
|                       [C6276](../code-quality/c6276.md)                        |                                              Geçersiz dize dönüştürme                                              |
|                       [C6277](../code-quality/c6277.md)                        |                                          Geçersiz CreateProcess çağrısı                                           |
|                       [C6284](../code-quality/c6284.md)                        |                                  Biçimlendirme Işlevine geçersiz nesne değişkeni                                   |
|                       [C6290](../code-quality/c6290.md)                        |                                      Mantıksal değil bit düzeyinde and önceliği                                       |
|                       [C6291](../code-quality/c6291.md)                        |                                       Mantıksal değil bit düzeyinde OR önceliği                                       |
|                       [C6302](../code-quality/c6302.md)                        |                             Biçimlendirme Işlevine geçersiz karakter dizesi değişkeni                              |
|                       [C6303](../code-quality/c6303.md)                        |                           Biçimlendirme Işlevine geçersiz geniş karakter dizesi değişkeni                           |
|                       [C6305](../code-quality/c6305.md)                        |                                         Eşleşmeyen boyut ve sayı kullanımı                                         |
|                       [C6306](../code-quality/c6306.md)                        |                                   Değişken bağımsız değişken Işlev çağrısı yanlış                                   |
|                       [C6328](../code-quality/c6328.md)                        |                                       Olası bağımsız değişken türü uyumsuzluğu                                        |
|                       [C6385](../code-quality/c6385.md)                        |                                                 Okuma taşması                                                  |
|                       [C6386](../code-quality/c6386.md)                        |                                                 Yazma taşması                                                 |
|                       [C6387](../code-quality/c6387.md)                        |                                            Geçersiz parametre değeri                                            |
|                       [C6500](../code-quality/c6500.md)                        |                                          Geçersiz öznitelik özelliği                                           |
|                       [C6501](../code-quality/c6501.md)                        |                                     Çakışan öznitelik özellik değerleri                                     |
|                       [C6503](../code-quality/c6503.md)                        |                                           Başvurular null olamaz                                           |
|                       [C6504](../code-quality/c6504.md)                        |                                              Işaretçi olmayan üzerinde null                                              |
|                       [C6505](../code-quality/c6505.md)                        |                                               Void üzerinde MustCheck                                               |
|                       [C6506](../code-quality/c6506.md)                        |                                      Işaretçi olmayan veya dizide arabellek boyutu                                      |
| [C6507](https://msdn.microsoft.com/18f88cd1-d035-4403-a6a4-12dd0affcf21)        |                                       Sıfır başvurusu sırasında null uyumsuzluğu                                       |
|                       [C6508](../code-quality/c6508.md)                        |                                           Sabit üzerinde yazma erişimi                                            |
|                       [C6509](../code-quality/c6509.md)                        |                                          Ön koşul üzerinde kullanılan dönüş                                          |
|                       [C6510](../code-quality/c6510.md)                        |                                        Işaretçili olmayan boş değer sonlandırıldı                                         |
|                       [C6511](../code-quality/c6511.md)                        |                                          MustCheck Evet veya Hayır olmalıdır                                          |
|                       [C6513](../code-quality/c6513.md)                        |                                       Arabellek boyutu olmadan öğe boyutu                                        |
|                       [C6514](../code-quality/c6514.md)                        |                                        Arabellek boyutu, dizi boyutunu aşıyor                                         |
|                       [C6515](../code-quality/c6515.md)                        |                                          Işaretçi olmayan ara bellek boyutu                                           |
|                       [C6516](../code-quality/c6516.md)                        |                                          Öznitelikte özellik yok                                           |
|                       [C6517](../code-quality/c6517.md)                        |                                       Okunabilir olmayan arabellekte geçerli boyut                                       |
|                       [C6518](../code-quality/c6518.md)                        |                                     Yazılabilir olmayan arabellekte yazılabilir boyut                                      |
| [C6521](https://msdn.microsoft.com/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)  |                                        Geçersiz boyut dizesi başvurusu                                        |
|                       [C6522](../code-quality/c6522.md)                        |                                           Geçersiz boyut dize türü                                            |
| [C6523](https://msdn.microsoft.com/11397a31-b224-46b0-afb7-d49ca576a3bb)  |                                         Geçersiz boyut dize parametresi                                         |
|                       [C6525](../code-quality/c6525.md)                        |                                   Geçersiz boyut dizesine ulaşılamıyor konumu                                    |
| [C6526](https://msdn.microsoft.com/59c590c7-0098-4166-a1ac-87f324596002)  |                                        Geçersiz boyut dizesi arabellek türü                                        |
|                       [C6527](../code-quality/c6527.md)                        |              Geçersiz ek açıklama: ' gereksiz Srelease ' özelliği void türünün değerleri üzerinde kullanılamaz               |
|                       [C6530](../code-quality/c6530.md)                        |                                       Tanınmayan biçim dizesi stili                                        |
|                       [C6540](../code-quality/c6540.md)                        | Bu işlev üzerinde öznitelik ek açıklamaları kullanımı, var olan tüm __declspec ek açıklamalarını geçersiz kılar  |
|                       [C6551](../code-quality/c6551.md)                        |                              Geçersiz boyut belirtimi: ifade ayrıştırılamıyor                              |
|                       [C6552](../code-quality/c6552.md)                        |                              Geçersiz Deref = veya Notref =: ifade ayrıştırılamıyor                               |
|                       [C6701](../code-quality/c6701.md)                        |                                  Değer geçerli bir Evet/Hayır/belki değeri değil                                  |
|                       [C6702](../code-quality/c6702.md)                        |                                        Değer bir dize değeri değil                                        |
|                       [C6703](../code-quality/c6703.md)                        |                                           Değer bir sayı değil                                           |
|                       [C6704](../code-quality/c6704.md)                        |                                    Beklenmeyen ek açıklama Ifadesi hatası                                     |
|                       [C6705](../code-quality/c6705.md)                        |     Ek açıklama için beklenen bağımsız değişken sayısı, ek açıklama için gerçek bağımsız değişken sayısıyla eşleşmiyor      |
|                       [C6706](../code-quality/c6706.md)                        |                                  Ek açıklama için beklenmeyen ek açıklama hatası                                   |
|                      [C28021](../code-quality/c28021.md)                       |                                Açıklama eklenen parametrenin bir işaretçi olması gerekir                                |
|                      [C28182](../code-quality/c28182.md)                       |         NULL işaretçiyle başvuruluyor. İşaretçi, başka bir işaretçi ile aynı NULL değeri içeriyor.          |
|                      [C28202](../code-quality/c28202.md)                       |                                    Statik olmayan üyeye geçersiz başvuru                                     |
|                      [C28203](../code-quality/c28203.md)                       |                                     Sınıf üyesine belirsiz başvuru.                                      |
|                      [C28205](../code-quality/c28205.md)                       |                           \_\_ \_ \_ Geçersiz bağlamda kullanılan başarılı veya On_failure                            |
|                      [C28206](../code-quality/c28206.md)                       |                                   Sol işlenen bir yapıya işaret ediyor, '-> ' kullanın                                   |
|                      [C28207](../code-quality/c28207.md)                       |                                       Sol işlenen bir struct, '. ' kullanın                                       |
|                      [C28210](../code-quality/c28210.md)                       |                 __On_failure bağlamı için ek açıklamalar açık bir ön bağlamda olmamalıdır                  |
|                      [C28211](../code-quality/c28211.md)                       |                                 SAL_context için beklenen statik bağlam adı                                  |
|                      [C28212](../code-quality/c28212.md)                       |                                  Ek açıklama için beklenen işaretçi ifadesi                                   |
|                      [C28213](../code-quality/c28213.md)                       | \_Use_decl_annotations \_ ek açıklaması, değişiklik yapılmadan önceki bir bildirime başvurmak için kullanılmalıdır. |
|                      [C28214](../code-quality/c28214.md)                       |                                   Öznitelik parametresi adları P1 olmalıdır... P9 olmalıdır                                   |
|                      [C28215](../code-quality/c28215.md)                       |                    Typedüzeltmesini zaten bir tür düzeltmesine sahip olan bir parametreye uygulanamaz                    |
|                      [C28216](../code-quality/c28216.md)                       |        CheckReturn ek açıklaması yalnızca belirli işlev parametresi için Sonkoşulları için geçerlidir.         |
|                      [C28217](../code-quality/c28217.md)                       |            İşlev için, ek açıklamanın parametre sayısı dosyada bulunan ile eşleşmiyor             |
|                      [C28218](../code-quality/c28218.md)                       |             İşlev parametresi için ek açıklamanın parametresi dosyada bulunan ile eşleşmiyor              |
|                      [C28219](../code-quality/c28219.md)                       |                 Ek açıklamada parametre ek açıklaması için beklenen numaralandırma üyesi                 |
|                      [C28220](../code-quality/c28220.md)                       |                  Ek açıklamada parametre ek açıklaması için beklenen tamsayı ifadesi                   |
|                      [C28221](../code-quality/c28221.md)                       |                        Ek açıklamada parametre için beklenen dize ifadesi                         |
|                      [C28222](../code-quality/c28222.md)                       |                               \_ek açıklama için __yes, _No veya \_ _maybe bekleniyor                               |
|                      [C28223](../code-quality/c28223.md)                       |                       Ek açıklama, parametre için beklenen belirteç/tanımlayıcı bulunamadı                        |
|                      [C28224](../code-quality/c28224.md)                       |                                        Ek açıklama parametre gerektiriyor                                         |
|                      [C28225](../code-quality/c28225.md)                       |                     Ek açıklamada gerekli parametrelerin doğru sayısı bulunamadı                      |
|                      [C28226](../code-quality/c28226.md)                       |                          Ek açıklama aynı zamanda bir PrimOp olamaz (geçerli bildirimde)                          |
|                      [C28227](../code-quality/c28227.md)                       |                          Ek açıklama aynı zamanda bir PrimOp olamaz (önceki bildirime bakın)                           |
|                      [C28228](../code-quality/c28228.md)                       |                             Ek açıklama parametresi: ek açıklamalarda tür kullanılamaz                              |
|                      [C28229](../code-quality/c28229.md)                       |                                    Ek açıklama parametreleri desteklemiyor                                     |
|                      [C28230](../code-quality/c28230.md)                       |                                     Parametre türünün üyesi yok.                                      |
|                      [C28231](../code-quality/c28231.md)                       |                                       Ek açıklama yalnızca dizide geçerlidir                                       |
|                      [C28232](../code-quality/c28232.md)                       |                               herhangi bir ek açıklamaya ön, post veya deref uygulanmadı                               |
|                      [C28233](../code-quality/c28233.md)                       |                                    bir bloğa ön, sonrası veya deref uygulandı                                     |
|                      [C28234](../code-quality/c28234.md)                       |                              __at ifadesi geçerli işleve uygulanmıyor                               |
|                      [C28235](../code-quality/c28235.md)                       |                               İşlev bir ek açıklama olarak tek başına kullanılamaz                                |
|                      [C28236](../code-quality/c28236.md)                       |                                Ek açıklama bir ifadede kullanılamaz                                 |
|                      [C28237](../code-quality/c28237.md)                       |                              Parametresindeki ek açıklama artık desteklenmiyor                               |
|                      [C28238](../code-quality/c28238.md)                       |      Parametresindeki ek açıklamanın birden fazla değeri, stringValue ve longValue 'ı vardır. Paramn = xxx kullanın       |
|                      [C28239](../code-quality/c28239.md)                       |  Parametresindeki ek açıklamanın değeri, stringValue veya longValue; ve Paramn = xxx. Yalnızca paramn = xxx kullanın   |
|                      [C28240](../code-quality/c28240.md)                       |                             Parametresindeki ek açıklamanın param2 vardır ancak Param1 yok                              |
|                      [C28241](../code-quality/c28241.md)                       |                          Parametre üzerindeki işlev için ek açıklama tanınmıyor                           |
|                      [C28243](../code-quality/c28243.md)                       |   Parametresindeki işlev için ek açıklama, ek açıklama eklenmiş olarak daha fazla başvuru gerektiriyor   |
|                      [C28245](../code-quality/c28245.md)                       |                     İşlev açıklamasına yönelik ek açıklama ' this ' öğesini üye olmayan bir işlev üzerinde Tates                     |
|                      [C28246](../code-quality/c28246.md)                       |                İşlevin parametre ek açıklaması, parametrenin türü ile eşleşmiyor                 |
|                      [C28250](../code-quality/c28250.md)                       |                    İşlev için tutarsız ek açıklama: önceki örnekte hata var.                     |
|                      [C28251](../code-quality/c28251.md)                       |                       İşlev için tutarsız ek açıklama: Bu örnekte hata var.                       |
|                      [C28252](../code-quality/c28252.md)                       |           İşlev için tutarsız ek açıklama: parametre bu örnekteki başka bir ek açıklamaya sahip.           |
|                      [C28253](../code-quality/c28253.md)                       |           İşlev için tutarsız ek açıklama: parametre bu örnekteki başka bir ek açıklamaya sahip.           |
|                      [C28254](../code-quality/c28254.md)                       |                               dynamic_cast<> () ek açıklamalarda desteklenmez                                |
|                      [C28262](../code-quality/c28262.md)                       |                    Ek açıklama için işlevde bir sözdizimi hatası bulundu                     |
|                      [C28263](../code-quality/c28263.md)                       |                 Iç ek açıklamanın koşullu ek açıklamasında söz dizimi hatası bulundu                 |
|                      [C28267](../code-quality/c28267.md)                       |                    Ek açıklamalarda bir söz dizimi hatası bulundu.                    |
|                      [C28272](../code-quality/c28272.md)                       |      İşlevi için ek açıklama, incelenirken parametresi, işlev bildirimiyle tutarsız      |
|                      [C28273](../code-quality/c28273.md)                       |                    İşlev için, ipuçları işlev bildirimiyle tutarsız                     |
|                      [C28275](../code-quality/c28275.md)                       |                                   \_Macro_value parametresi \_ null                                    |
|                      [C28279](../code-quality/c28279.md)                       |                           Sembol için, eşleşen bir ' End ' olmadan bir ' begin' bulundu                            |
|                      [C28280](../code-quality/c28280.md)                       |                           Sembol için, eşleşen bir ' begin' olmadan bir ' End ' bulundu                           |
|                      [C28282](../code-quality/c28282.md)                       |                                    Biçim dizeleri ön koşullarda olmalıdır                                    |
|                      [C28285](../code-quality/c28285.md)                       |                                    İşlev için, parametrede söz dizimi hatası                                    |
|                      [C28286](../code-quality/c28286.md)                       |                                    İşlev için, sonda yakınında sözdizimi hatası                                    |
|                      [C28287](../code-quality/c28287.md)                       |                İşlev için, \_ at \_ () ek açıklamasında söz dizimi hatası (Tanınmayan parametre adı)                |
|                      [C28288](../code-quality/c28288.md)                       |                  İşlev için, \_ at \_ () ek açıklamasında söz dizimi hatası (geçersiz parametre adı)                   |
|                      [C28289](../code-quality/c28289.md)                       |                İşlev için: ReadableTo veya WritableTo parametre olarak bir limit-spec içermiyordu                |
|                      [C28290](../code-quality/c28290.md)                       |           işlev için ek açıklama, gerçek parametre sayısından daha fazla dışlar içeriyor            |
|                      [C28291](../code-quality/c28291.md)                       |                        deref düzey 0 ' da null/NotNull Post işlevi için anlamsız bir küçüktür.                        |
|                      [C28300](../code-quality/c28300.md)                       |                            İşleç için uyumsuz türlerin ifade işlenenleri                             |
|                      [C28301](../code-quality/c28301.md)                       |                               İşlevin ilk bildirimi için ek açıklama yok.                               |
|                      [C28302](../code-quality/c28302.md)                       |                             \_Ek açıklamada ek bir deref \_ işleci bulundu.                              |
|                      [C28303](../code-quality/c28303.md)                       |                           \_Ek açıklamada belirsiz bir deref \_ işleci bulundu.                            |
|                      [C28304](../code-quality/c28304.md)                       |                     Belirtece hatalı yerleştirilmiş \_ Notref \_ işleci bulundu.                      |
|                      [C28305](../code-quality/c28305.md)                       |                                Belirteç ayrıştırılırken bir hata bulundu.                                 |
|                      [C28350](../code-quality/c28350.md)                       |                  Ek açıklama koşullu olarak uygulanabilir olmayan bir durum tanımlar.                   |
|                      [C28351](../code-quality/c28351.md)                       |         Ek açıklama, koşulda bir dinamik değerin (bir değişken) kullanılamayacağını açıklar.          |
