---
title: VSPackage için yükleme dizinini seçme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ead19e9f50201ab795e3c3f68b661037d309d98d
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011911"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>VSPackage için yükleme dizinini seçin
Bir VSPackage ve destekleyici dosyaları bir kullanıcının dosya sisteminde olmalıdır. Konum, VSPackage 'ın yönetilip yönetilmediğini, yan yana sürüm oluşturma şemanızın ve Kullanıcı tercihinizin olup olmamasına bağlıdır.

## <a name="unmanaged-vspackages"></a>Yönetilmeyen VSPackages
 Yönetilmeyen VSPackage, herhangi bir konuma yüklenebilen bir COM sunucusudur. Kayıt bilgileri, konumunu doğru şekilde yansıtmalıdır. Yükleyici Kullanıcı arabiriminiz (UI), Windows Installer özellik değerinin alt dizini olarak varsayılan bir konum sağlamalıdır `ProgramFilesFolder` . Örneğin:

*&lt;ProgramFilesFolder &gt; \\ &lt; şirketim &gt; \\ &lt; myvspackageproduct &gt; \v1.0\\*

 Kullanıcının küçük bir önyükleme bölümünü tutan ve başka bir birime uygulama ve araç yüklemeyi tercih ettiği kullanıcılara uyum sağlaması için varsayılan dizini değiştirmesine izin verilmelidir.

 Yan yana şemanızın sürümü sürümlü bir VSPackage kullanıyorsa, farklı sürümleri depolamak için alt dizinleri kullanabilirsiniz. Örneğin:

 *&lt;ProgramFilesFolder &gt; \\ &lt; şirketim &gt; \\ &lt; myvspackageproduct &gt; \\ v 1.0 \\ 2002\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; şirketim &gt; \\ &lt; myvspackageproduct &gt; \\ v 1.0 \\ 2003\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; şirketim &gt; \\ &lt; myvspackageproduct &gt; \\ v 1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>Yönetilen VSPackages
 Yönetilen VSPackages, herhangi bir konuma de yüklenebilir. Ancak, derleme yükleme sürelerini azaltmak için bunları her zaman genel derleme önbelleği 'ne (GAC) yüklemeyi düşünmelisiniz. Yönetilen VSPackages, her zaman güçlü adlandırılmış derlemeler olduğundan, bunları GAC 'ye yüklemek, tanımlayıcı ad imzası doğrulamanın yalnızca yükleme sırasında aldığı anlamına gelir. Dosya sisteminde başka bir yerde yüklü olan güçlü adlandırılmış derlemelerin imzaları her yüklenilişinde bunların doğrulanması gerekir. GAC 'de Yönetilen VSPackages yüklediğinizde, derlemenin tanımlayıcı adına işaret eden kayıt defteri girişlerini yazmak için RegPkg aracının **/Assembly** anahtarını kullanın.

 Yönetilen VSPackages 'yi GAC dışında bir konuma yüklerseniz, Dizin hiyerarşilerini seçmek için Yönetilmeyen VSPackages için verilen önceki önerileri izleyin. VSPackage derlemesinin yolunu işaret eden kayıt defteri girişlerini yazmak için RegPkg aracının **/CODEBASE** anahtarını kullanın.

 Daha fazla bilgi için bkz. [VSPackages 'ı kaydetme ve kaydını kaldırma](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Uydu DLL'leri
 Kural gereği, belirli bir yerel ayara yönelik kaynakları içeren VSPackage uydu dll 'Leri *VSPackage* dizininin alt dizinlerinde bulunur. Alt dizinler yerel ayar KIMLIĞI (LCıD) değerlerine karşılık gelir.

 [Manage VSPackages](../../extensibility/managing-vspackages.md) makalesinde, kayıt defteri girdileri, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aslında bir VSPackage 'ın uydu dll 'inin nerede göründüğünü kontrol gösterir. Ancak, bir kültür DLL 'sini bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] LCID değeri için adlı bir alt dizine aşağıdaki sırayla yüklemeye çalışır:

1. Varsayılan LCıD (Visual Studio LCıD; Örneğin, Ingilizce için *\ 1033* )

2. Varsayılan alt dille varsayılan LCıD.

3. Sistem varsayılan LCıD 'SI.

4. Varsayılan alt dille sistem varsayılan LCıD 'SI.

5. ABD Ingilizcesi (*. \ 1033* veya *.\0x409*).

VSPackage DLL 'niz kaynakları içeriyorsa ve **SatelliteDll\DllName** kayıt defteri girişi işaret ediyorsa, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bunları yukarıdaki sırayla yüklemeye çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [Paylaşılan ve sürümlenmiş VSPackages arasında seçim yapın](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
- [Paket kaydını yönetme](/previous-versions/bb166783(v=vs.100))