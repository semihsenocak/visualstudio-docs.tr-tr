---
title: 'Nasıl yapılır: paket bildirimi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153833"
---
# <a name="how-to-create-a-package-manifest"></a>Nasıl yapılır: Paket Bildirimi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanıza yönelik önkoşulları dağıtmak için bir önyükleyici paketi kullanabilirsiniz. Önyükleyici paketi tek bir ürün bildirim dosyası, ancak her yerel ayar için bir paket bildirimi içerir. Farklı yerelleştirilmiş sürümler genelinde paylaşılan işlevsellik ürün bildirimine gitmelidir.  
  
 Paket bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Paket bildirimi oluşturuluyor  
  
#### <a name="to-create-the-package-manifest"></a>Paket bildirimi oluşturmak için  
  
1. Önyükleyici paketi için bir dizin oluşturun. Bu örnek C:\packagekullanır.  
  
2. Yerel ayar adına sahip bir alt dizin oluşturun (örneğin, Ingilizce için).  
  
3. Visual Studio 'da adlı bir XML dosyası oluşturun `package.xml` ve C:\package\en klasörüne kaydedin.  
  
4. Önyükleyici paketinin adını, bu yerelleştirilmiş paket bildirimi için kültürü ve isteğe bağlı lisans sözleşmesini listelemek için XML ekleyin. Aşağıdaki XML, `DisplayName` ve `Culture` daha sonraki bir öğesinde tanımlanan değişkenleri kullanır.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Yerel ayara özgü dizindeki tüm dosyaları listelemek için XML ekleyin. Aşağıdaki XML, **en** yerel ayar için geçerli olan eula.txt adında bir dosya kullanır.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Önyükleyici paketi için yerelleştirilebilir dizeler tanımlamak üzere XML ekleyin. Aşağıdaki XML, en yerel ayar için hata dizelerini ekler.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. C:\Package klasörünü Visual Studio önyükleyici dizinine kopyalayın. Visual Studio 2010 için bu, \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages dizinidir.  
  
## <a name="example"></a>Örnek  
 Paket bildirimi, hata iletileri, yazılım lisans koşulları ve dil paketleri gibi yerel ayara özgü bilgiler içerir.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ürün ve Paket Şema Başvurusu](../deployment/product-and-package-schema-reference.md)
