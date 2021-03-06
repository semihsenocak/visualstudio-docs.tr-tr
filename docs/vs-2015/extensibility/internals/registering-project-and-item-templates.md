---
title: Proje ve öğe şablonlarını kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185830"
---
# <a name="registering-project-and-item-templates"></a>Proje ve Öğe Şablonlarını Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje türleri, proje ve proje öğesi şablonlarının bulunduğu dizinleri kaydetmelidir. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , **Yeni Proje Ekle** ve **Yeni öğe Ekle** iletişim kutularında nelerin gösterileceğini belirlemek için proje türleriniz ile ilişkili kayıt bilgilerini kullanır.  
  
 Şablonlar hakkında daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Projeler için kayıt defteri girişleri  
 Aşağıdaki örneklerde HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *Sürüm*> altında kayıt defteri girişleri gösterilmektedir. Eşlik eden tablolar örneklerde kullanılan öğeleri açıklar.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|@|REG_SZ|Bu türden projelerin varsayılan adı.|  
|DisplayName|REG_SZ|Paketler altında kayıtlı olan uydu DLL 'sinden alınacak adın kaynak KIMLIĞI.|  
|Paket|REG_SZ|Paketler altına kayıtlı paketin sınıf KIMLIĞI.|  
|ProjectTemplates dir|REG_SZ|Proje şablonu dosyalarının varsayılan yolu. Proje şablonu dosyaları **Yeni proje** şablonu tarafından görüntülenir.|  
  
### <a name="registering-item-templates"></a>Öğe şablonlarını kaydetme  
 Öğe şablonlarını depoladığınız dizini kaydetmeniz gerekir.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|@|REG_SZ|Öğe şablonları eklemek için kaynak KIMLIĞI.|  
|Templates dizini|REG_SZ|**Yeni öğe Ekle** sihirbazının iletişim kutusunda görünen proje öğelerinin yolu.|  
|Templates Localizedsubdir|REG_SZ|Yerelleştirilmiş şablonları tutan Templates dizini 'nin alt dizinini isimeden bir dizenin kaynak KIMLIĞI. , [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Varsa, uydu dll 'lerinden dize kaynağını yükler, her uydu dll farklı bir yerelleştirilmiş alt dizin adı içerebilir.|  
|SortPriority|REG_DWORD|**Yeni öğe Ekle** iletişim kutusunda Şablonların gösterileceği sırayı yönetmek Için SortPriority ayarlayın. Daha önce şablon listesinde daha büyük SortPriority değerleri görünür.|  
  
### <a name="registering-file-filters"></a>Dosya filtrelerini kaydetme  
 İsteğe bağlı olarak, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dosya adlarını sorulduğunda kullanan filtreleri kaydedebilirsiniz. Örneğin, [!INCLUDE[csprcs](../../includes/csprcs-md.md)] **Dosya Aç** iletişim kutusu için filtre:  
  
 **Visual C# dosyaları ( \* . cs, \* . resx, \* . Settings, \* . xsd, \* . wsdl); \* . CS, \* . resx, \* . Settings, \* . xsd, \* . wsdl)**  
  
 Birden çok filtrenin kaydedilmesini desteklemek için, her bir filtre HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *sürümü*> \projects \\ { \<*ProjectGUID*> } \filters \\ < *AltAnahtar*> altında kendi alt anahtarına kaydedilir. Alt anahtar adı rastgele; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] alt anahtarın adını yoksayar ve yalnızca kendi değerlerini kullanır.  
  
 Aşağıdaki tabloda gösterilen bayraklar ayarlanarak bir filtrenin kullanıldığı bağlamların denetimini yapabilirsiniz. Bir filtrenin bayrak ayarlanmamışsa, **Varolan öğe Ekle** iletişim kutusunda ve **Dosya Aç** iletişim kutusunda ortak filtrelerden sonra listelenir, ancak **dosyalarda bul** iletişim kutusunda kullanılmaz.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|Commonfindfilesfiltresi|REG_DWORD|**Dosyalarda bul** iletişim kutusunda ortak filtrelerden birine filtre uygular. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|  
|Commonopenfilesfiltresi|REG_DWORD|**Dosya Aç** iletişim kutusunda ortak filtrelerden birine filtre uygular. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|  
|Finınfilesfiltresi|REG_DWORD|**Dosyalarda bul** iletişim kutusunda ortak filtrelerden sonra filtreyi listeler.|  
|NotOpenFileFilter|REG_DWORD|Filtrenin **Dosya Aç** iletişim kutusunda kullanılmadığını gösterir.|  
|Notaddexistingıtemfilter|REG_DWORD|Filtrenin **Varolan öğe Ekle** iletişim kutusunda kullanılmadığını gösterir.|  
|SortPriority|REG_DWORD|Filtrelerin gösterileceği sırayı yönetmek için SortPriority ayarlayın. Daha büyük SortPriority değerleri, daha önce filtre listesinde görünür.|  
  
## <a name="directory-structure"></a>Dizin yapısı  
 VSPackages, konum tümleşik geliştirme ortamı (IDE) ile kaydedildiği sürece, şablon dosyalarını ve klasörlerini yerel veya uzak bir diskte herhangi bir yere yerleştirebilir. Ancak kuruluş kolaylığı için, ürününüzün yükleme yolu altında aşağıdaki dizin yapısını öneririz.  
  
 \ Şablonlar  
  
 \Projects (proje şablonlarını içerir)  
  
 \ Uygulamalar  
  
 \ Bileşenler  
  
 \ ...  
  
 \Projectıtems (proje öğelerini içerir)  
  
 \Class  
  
 \ Form  
  
 \Web sayfası  
  
 \ Helperfiles (birden çok dosya proje öğelerinde kullanılan dosyaları içerir)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 ['Nı](../../extensibility/internals/wizards.md)   
 [Uygulamaları Yerelleştirme](../../ide/localizing-applications.md)   
 [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
