---
title: C++ projelerinde hata ayıklamaya hazırlanma | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: dc663115e98d7553e03a186874d59b75eb68cb90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916317"
---
# <a name="debugging-preparation-c-project-types"></a>Hata Ayıklama Hazırlığı: C++ proje türleri
Bu bölümde, proje şablonları tarafından oluşturulan temel proje türlerinde hata ayıklama işlemlerinin nasıl yapılacağı açıklanmaktadır [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .

 Kendi çıktıları olarak DLL 'Ler oluşturan proje türlerinin, paylaştığı ortak özellikler nedeniyle [hata ayıklama dll projelerinde](../debugger/debugging-dll-projects.md) gruplandırıldığını unutmayın.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 [Önerilen özellik ayarları](#BKMK_Recommended_Property_Settings)

 [Win32 projeleri](#BKMK_Win32_Projects)

- [C veya C++ Win32 uygulamasında hata ayıklamak için](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Bir hata ayıklama yapılandırmasını el ile ayarlamak için](#BKMK_To_manually_set_a_Debug_configuration)

  [Windows Forms uygulamalar (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Önerilen özellik ayarları
 Bazı özellikler, tüm yönetilmeyen hata ayıklama senaryolarında aynı şekilde ayarlanmalıdır. Aşağıdaki tablolarda önerilen özellik ayarları görüntülenir. Burada listelenmeyen ayarlar, farklı yönetilmeyen proje türleri arasında farklılık gösterebilir. Daha fazla bilgi için bkz. [C++ hata ayıklama yapılandırması Için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Yapılandırma özellikleri &#124; C/C++ &#124; Iyileştirme düğümü

|Özellik Adı|Ayar|
|-------------------|-------------|
|**İyileştirme**|**Devre dışı olarak ayarla (/0d).** Üretilen yönergeler doğrudan kaynak kodunuza karşılık gelmediğinden, iyileştirilmiş kodun hata ayıklama işlemi daha zordur. Programınızın yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata olduğunu fark ederseniz, bu ayarı açabilirsiniz, ancak **ayrıştırma** penceresinde gösterilen kodun, kaynak pencerenize gördüklerinize uygun olmayan en iyi duruma getirilmiş kaynaktan oluşturulduğunu unutmayın. Adımlama gibi diğer özellikler beklendiği gibi davranmayabilir.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Yapılandırma özellikleri &#124; bağlayıcı &#124; hata ayıklama düğümü

|Özellik Adı|Ayar|
|-------------------|-------------|
|**Hata ayıklama bilgileri oluştur**|Hata ayıklama sembolleri ve hata ayıklama için gereken dosyaları oluşturmak için her zaman bu seçeneği **Evet (/Debug)** olarak ayarlamanız gerekir. Uygulama üretime geçtiğinde, onu kapalı olarak ayarlayabilirsiniz.|

 [Bu konuda](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Win32 projeleri
 Win32 uygulamaları, C veya C++ dilinde yazılmış geleneksel Windows programlarıdır. İçinde bu tür bir uygulama hata ayıklaması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] basittir.

 Win32 uygulamaları MFC uygulamalarını ve ATL projelerini içerir. Bunlar Windows API 'Lerini kullanır ve MFC veya ATL kullanabilir, ancak ortak dil çalışma zamanını (CLR) kullanmaz. Ancak, CLR kullanan yönetilen kodu çağırabilir.

 Aşağıdaki yordamda içinden bir Win32 projesinde hata ayıklama işlemi açıklanmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bir Win32 uygulamasında hata ayıklamanın başka bir yolu da uygulamayı dışında başlatmak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve bu uygulamaya eklemektir. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> C veya C++ Win32 uygulamasında hata ayıklamak için

1. Projeyi Visual Studio'da açın.

2. **Hata Ayıkla** menüsünde **Başlat**' ı seçin.

3. Hata [ayıklayıcıyla ilk bakış](../debugger/debugger-feature-tour.md)bölümünde açıklanan teknikleri kullanarak hata ayıklayın.

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Bir hata ayıklama yapılandırmasını el ile ayarlamak için

1. **Görünüm** menüsünde, **Özellik sayfaları**' na tıklayın.

2. Henüz yoksa açmak için **yapılandırma özellikleri** düğümüne tıklayın

3. **Genel**' i seçin ve **Çıkış** satırının değerini **Hata Ayıkla**olarak ayarlayın.

4. **C/C++** düğümünü açın ve **genel**' i seçin.

    **Hata ayıklama** satırında, derleyici tarafından oluşturulacak hata ayıklama bilgilerinin türünü belirtirsiniz. **Program veritabanı (/Zi)** veya **Düzenle & devam et için program veritabanı (/Zi)** arasından seçim yapabilirsiniz.

5. **İyileştirme**' yi seçin ve **iyileştirme** satırında, açılır listeden **devre dışı (/0d)** seçeneğini belirleyin.

    Üretilen yönergeler doğrudan kaynak kodunuza karşılık gelmediğinden, iyileştirilmiş kodun hata ayıklama işlemi daha zordur. Programınızın yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata olduğunu fark ederseniz, bu ayarı açabilirsiniz, ancak ayrıştırma penceresinde gösterilen kodun, kaynak pencerenize gördüklerinize uygun olmayan en iyi duruma getirilmiş kaynaktan oluşturulduğunu unutmayın. Adımlama gibi özellikler büyük olasılıkla kesme noktaları ve yürütme noktası yanlış gösterilebilir.

6. **Bağlayıcı** düğümünü açın ve **hata ayıklama**öğesini seçin. İlk **Oluştur** satırında, açılan listeden **Evet (/Debug)** öğesini seçin. Hata ayıklama sırasında her zaman ayarlayın.

   Daha fazla bilgi için bkz.[C++ hata ayıklama yapılandırması Için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [Bu konuda](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="windows-forms-applications-net"></a><a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Forms uygulamalar (.NET)
 **Windows Forms uygulaması (.net)** şablonu, bir [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Windows Forms uygulaması oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: Windows uygulaması projesi oluşturma](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 İçindeki bu tür bir uygulama hata ayıklaması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , yönetilen Windows Forms uygulamalarında benzerdir.

 Proje şablonuyla bir Windows Forms projesi oluşturduğunuzda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otomatik olarak hata ayıklama ve sürüm yapılandırması için gerekli ayarları oluşturur. Gerekirse, bu ayarları ** \<project name> Özellik sayfaları** iletişim kutusunda değiştirebilirsiniz. Daha fazla bilgi için bkz. [hata ayıklama ve yayın yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md).

 Daha fazla bilgi için bkz. [C++ hata ayıklama yapılandırması Için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Windows Forms bir uygulamada hata ayıklamanın başka bir yolu da uygulamanın dışında başlatılması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve bu uygulamaya iliştirmenin bir yoludur. Daha fazla bilgi için bkz. [çalışan bir programa veya birden çok programa ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [Bu konuda](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Çalışan bir programa veya birden çok programa ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata ayıklama ve sürüm yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md)
- [Nasıl yapılır: Windows uygulaması projesi oluşturma](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))