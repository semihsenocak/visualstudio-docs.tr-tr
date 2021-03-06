---
title: UWP uygulamaları için uygulama Özellik sayfası
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3c8f72d4e1d1caeacd5dfefef5310dc2cef83b92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77173084"
---
# <a name="application-property-page-uwp-projects"></a>Uygulama özellik sayfası (UWP projeleri)

Evrensel Windows Platformu (UWP) projesinin derleme ve paket bilgilerini belirtmek ve Windows 10 sürümünü hedeflemek için **uygulama** özelliği sayfasını kullanın.

![Uygulama özellik sayfası](media/application-page-uwp.png)

**Uygulama** sayfasına erişmek için **Çözüm Gezgini**içinde proje düğümünü seçin. Ardından **Project**  >  , menü çubuğunda Proje**özellikleri** ' ni seçin. Özellik sayfaları **uygulama** sekmesinde açılır.

## <a name="general-section"></a>Genel Bölüm

**Bütünleştirilmiş kod adı** &mdash; Derleme bildirimini tutacak çıkış dosyasının adını belirtir.

Programlı olarak bu özelliğe erişmek için bkz <xref:VSLangProj.ProjectProperties.AssemblyName%2A> ..

**Varsayılan ad alanı** &mdash; Projeye eklenen dosyalar için temel ad alanını belirtir. Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/namespaces/), [ad alanları (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)veya [ad alanları (C++)](/cpp/cpp/namespaces-cpp).

Programlı olarak bu özelliğe erişmek için bkz <xref:VSLangProj.ProjectProperties.RootNamespace%2A> ..

**Derleme bilgileri** &mdash; Bu düğme seçildiğinde, [derleme bilgileri iletişim kutusu](../../ide/reference/assembly-information-dialog-box.md)görüntülenir.

**Paket bildirimi** &mdash; Bu düğme seçildiğinde, bildirim Tasarımcısı açılır. Bildirim tasarımcısına Ayrıca **Çözüm Gezgini** _Package. appxmanifest_ dosyası seçilerek de erişilebilir. Daha fazla bilgi için bkz. [bildirim Tasarımcısı ile paket yapılandırma](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Hedefleme bölümü

Bu bölümdeki açılan listeleri kullanarak uygulamanız için Windows 10 ' un hedef sürümünü ve en düşük sürümünü ayarlayabilirsiniz. Windows 10 ' un en son sürümünü hedefliyorsanız ve bir kurumsal uygulama geliştiriyorsanız, daha eski bir sürümü çok daha destekliyorsanız önerilir. Hangi Windows 10 sürümü seçeceğiniz hakkında daha fazla bilgi için bkz. [UWP sürümü seçme](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Visual Studio 'da Platform hedefleme hakkında daha fazla bilgi için bkz. [Platform hedefleme](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Ayrıca bkz.

- [İlk UWP uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)
- [UWP sürümü seçin](/windows/uwp/updates-and-versions/choose-a-uwp-version)
