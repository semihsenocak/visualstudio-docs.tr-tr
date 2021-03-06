---
title: Desteklenen Visual Studio özellikleri (Önizleme)
description: GitHub Codespaces ile çalışırken kullanılabilecek Visual Studio IDE özellikleri hakkında bilgi edinin.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c86fc99fe6bd2ae17b6ce222b04549db07d7687e
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90862272"
---
# <a name="supported-visual-studio-features-preview"></a>Desteklenen Visual Studio özellikleri (Önizleme)

Visual Studio, bir codespace 'e bağlanırken zengin bir geliştirme deneyimi sağlar. Kaynak kodunuzu düzenleme, hata ayıklama, test etme ve sürüm ile proje şablonları, zengin kod gezintisi ve IntelliSense gibi üretkenlik özelliklerini düzenlemek için bildiğiniz Visual Studio iç döngüsü araçlarını edinin.

Geçerli GitHub Codespaces [genel beta](https://github.com/features/codespaces)sürümünde bazı Visual Studio özellikleri tam desteğe sahip olmayabilir veya başlangıçta eksik olabilir. Aşağıdaki bölümlerde, Visual Studio ve GitHub Codespaces Beta ile neler beklediğinizi ve gelecekte neler görebileceğinize ilişkin ana hatlarıyla yer verilmiştir. 

Bu, geniş **kapsamlı bir liste olması anlamına gelir**, ancak bir codespace 'e bağlandığında Visual Studio 'nun genel yeteneklerini açıklamaktadır.

> [!NOTE]
> Visual Studio ile codespaces kullanırken eksik bir özellik varsa, lütfen üzerinde bir sorun açarak bize bildirin https://developercommunity.visualstudio.com/ . Bu, en çok istenen özellikleri önceliklendirmemize yardımcı olur.

> [!NOTE]
> Aşağıda açıklanan özellikler, diğer iki GitHub Codespaces istemcisi değil, Visual Studio içindir; Visual Studio Code ve tarayıcı içi düzenleyici.

## <a name="edit-and-navigation"></a>Düzenle ve gezinti

IntelliSense, kod gezintisi, Tanılamalar ve öneriler gibi akıllı dil özellikleri alırken codespace 'te kaynak kodu düzenlemenin küçük bir fark olduğuna dikkat etmeniz gerekir.

* IntelliSense
* Kod gezintisi *
* Biçim belgesiyle kod biçimlendirme
* Söz dizimi vurgulama
* Hızlı bilgi *
* HTML, CSS, Razor düzenleyicileri *-kısmi destek.
* JavaScript Düzenleyicisi *-kısmi destek.

Henüz kullanılabilir değil:

* IntelliSense *-bazı otomatik tamamlama/üye listesi filtreleri kullanılamıyor. İçeri aktarılmayan türler için tamamlama ve Gözcü penceresinde IntelliSense henüz kullanılamıyor.
* Kod gezintisi *-çoğu komut desteklenir, özellikle de yol belirtimine sahip dosyalardaki taban ve bulma özelliği henüz desteklenmiyor.
* Hızlı bilgi *-hızlı Info 'da renklendirme desteklenmez.
* HTML, CSS, Razor düzenleyicileri *-tanılama, IntelliSense tamamlama, hızlı bilgi, akıllı girinti. Şu anda anlam renklendirme, gezinme komutları vb. için destek yoktur.
* JavaScript Düzenleyicisi *-betik blokları (örneğin, HTML ve CSHTML dosyalarındaki JavaScript içeriği) ve anlam vurgulama henüz desteklenmemektedir. Ampul özellikleriyle ilgili bilinen sorunlar ve Özellikler.
* CMake hedefleri görünümü
* CMake proje ayarları Düzenleyicisi
* Ctrl + F7 (dosyayı Derle)
* CodeLens
* Kod parçacıkları
* IntelliCode

## <a name="application-types-and-configuration"></a>Uygulama türleri ve yapılandırma

Çoğu uygulama türü ve proje yapılandırması desteklenir, ancak doğrudan görsel tasarımcı yardımı olmadan proje kodunuzu düzenlemeniz gerekir. Daha fazla yapılandırma kılavuzu için bkz. [Kod alanını özelleştirme](customize-codespaces.md).

* Proje ve öğe şablonları
* .NET Core ve ASP.NET Core projeleri
* C++ konsol uygulamaları-CMake ve vcxproj destekleniyor
* Linux 'u hedefleyen C++ uygulamaları (çoğunlukla GUI olmayan için desteklenir). WSL 'yi, platforma özel IntelliSense 'i ve derlemeyi yükleyebilme ve sağlama özelliği.
* Proje dosyası düzenlemesi-çoğunlukla desteklenir. Bazı tamamlama, sözdizimi vurgulama ve gelişmiş Düzenle özellikleri eksik.
* GitHub hesapları-Codespaces oluşturup bağlanmak ve GitHub 'daki hesapta kullanılabilen kaynaklara erişmek için kullanılabilir.
* Azure CLı-oturum açmış Visual Studio kimliğini veya Anahtarlık hesaplarını paylaşmaz. Tarayıcı tabanlı oturum açma desteklenmez, ancak şunları kullanarak tümleşik Terminal içinde kimlik doğrulaması yapabilirsiniz: `az login --use-device-code` .

Henüz kullanılabilir değil:

* UI tasarımcıları-WinForms ve WPF tasarımcıları
* Visual Basic ve F # projeleri
* Hedeflenen projeleri .NET Framework
* Docker Compose projeleri
* Proje özellik sayfaları
* ASP.NET Core şablonlarındaki kimlik doğrulama seçenekleri
* Yükleme için GUI gerektiren uygulamalar-terminalle yüklenebilen her şey desteklenir (Chocolatey yükleyicisi dahil), ancak gerçek GUI hemen kullanılabilir olmaz. Gusıs 'e erişmek için tam ekran Live Share etkinleştirilmesi, geçerli bir geçici çözümdür. Yönetim konsolları erişilebilir değil. Yükleme için yeniden başlatma gerektiren uygulamalar desteklenmez.
* Visual Studio 'da Azure kaynakları için Yönetilen kimlikler
* Intranet kaynakları (özel ağ)-Şu anda codespaces, VPN gerektiren herhangi bir kaynağa bağlanamaz.
* Uzantılar-Visual Studio ile Codespaces kullanılırken hiçbir uzantı desteklenmez.

## <a name="debugging"></a>Hata Ayıklama

Önemli iç döngü hata ayıklaması, kesme noktaları, temel kod Adımlama, değişkenleri İnceleme ve yerel, oto ve izleme pencereleri dahil olmak üzere desteklenir. Bazı ek pencereler, özelleştirmeler ve Görselleştiriciler desteklenmez.

* Kesme noktaları
* Temel Adımlama
* Yereller, oto, pencereleri izle *-kısmi destek.
* Sembol sunucusu, kaynak sunucu ve içeri/dışarı aktarma veri ipuçları kısmen desteklenir.

Henüz kullanılabilir değil:

* Kesme noktaları *-kesme noktası etiketleri, veri kesme noktaları ve ayrıştırma kesme noktası ' nda bir işlem sürüyor. Kesme noktaları içeri ve dışarı aktarma kısmen desteklenir.
* Yereller, otomatik olarak Windows 'u izle *-arama kutusu ve arama kutusu gezintisinde ifade tamamlama gibi bazı işlevler.
* UI özelleştirmeleri-Pinınfor özellikleri ve şablon parametrelerinin gizlenmesi desteklenmez.
* Görselleştiriciler-C++ Natvis kısmen destekleniyor. Ayrıştırılmış pencere, XAML görsel tanılama, özel .NET Görselleştiriciler ve veri kümesi Görselleştiriciler desteklenmez.
* Ek hata ayıklayıcı pencereleri-Windows 'un kısmen desteklediği Işler. Paralel Yığınlar penceresi-görevler görünümü, Tanılama Merkezi ve kaynak/sembol bul iletişim kutusu desteklenmez.
* Bazı hata ayıklayıcı iş akışları-işleme Iliştirme, tam zamanında (JıT) hata ayıklayıcı, döküm hata ayıklama, profil oluşturma ve IntelliTrace desteklenmez. C++ Yalnızca kendi kodum Adımlama kısmen desteklenir.
* Düzenle ve devam et-hem yönetilen hem de yerel kod için desteklenmez.
* İş parçacığı özellikleri-iş parçacıklarını dondurma/çözme, iş parçacığını yeniden adlandırma ve iş parçacıklarını kaynakta gösterme desteklenmiyor.
* Ek Adımlama özellikleri-Özellikler ve işleçler üzerinde otomatik adım (.NET Core) ve Step to specific desteklenmez. 

## <a name="features"></a>Özellikler

Bir codespace 'e bağlı Visual Studio ile çalışırken, yerel olarak çalışırken aynı erişilebilirlik özelliklerini alırsınız.

* Kaynak denetimi-yeni [Git penceresi](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)aracılığıyla tam git desteği.
* Erişilebilirlik-yardımcı teknolojide, bir hata ayıklama uygulamasının appatama 'ya erişemediği bilinen bir sorun var. Bu sınırlamanın yanı sıra, yerel Visual Studio deneyiminde zaten mevcut olmayan başka uyumluluk sorunları olduğunu düşünmedik. [Geliştirici topluluğu](https://developercommunity.visualstudio.com/)'nda bir sorun oluşturarak hataları algılamadıysanız lütfen bize bildirin.
* Yayımlama-GitHub eylemleri aracılığıyla Azure 'da yayımlayın.
* Bağlı hizmetler-Application Insights, Keykasası, Storage, SQL, Redsıs, Cosmos, Openapı ve gRPC kısmen desteklenmektedir.
* Test Gezgini *-çoğunlukla desteklenir.

Henüz kullanılabilir değil:

* Test Gezgini *-varsayılan mimari seçimi gibi bazı özellikler, testleri paralel, çalma listeleri, vb. olarak çalıştırın. Birim testinde hata ayıklama ile ilgili bilinen sorunlar, çalışma ayarları ve bazı ek kurumsal özellikler. Profil oluşturma birim testleri desteklenmez.
* NuGet Paket Yöneticisi Kullanıcı arabirimi-NuGet komut satırı desteklenir.
* Kurumsal test özellikleri-Live Unit Testing, Microsoft Fakes, kod kapsamı ve IntelliTest desteklenmez.
* Gelişmiş yayımlama senaryoları-seçmeli yayımlama, FTP Yayımlama, önizleme değişiklikleri, hızlı yayınlama araç çubuğu vb.

## <a name="see-also"></a>Ayrıca bkz.

* [GitHub Codespaces nedir?](codespaces-overview.md)
* [Visual Studio 'Yu bir codespace ile kullanma](use-visual-studio-with-codespaces.md)
* [Codespace 'i özelleştirme](customize-codespaces.md)
