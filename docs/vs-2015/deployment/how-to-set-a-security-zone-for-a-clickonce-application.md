---
title: 'Nasıl yapılır: ClickOnce uygulaması için güvenlik bölgesi ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9af4507d7ccd604f82aae675bf87d36c0b039b26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68171422"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulaması için Bir Güvenlik Bölgesi Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce uygulaması için kod erişimi güvenlik izinlerini ayarlarken, **Proje Tasarımcısı**'nın **güvenlik** sayfasında bir temel izin kümesiyle başlamanız gerekir.  
  
 Çoğu durumda, sınırlı bir izin kümesi içeren **Internet** bölgesini veya daha büyük bir izin kümesi Içeren **Yerel Intranet** bölgesini de seçebilirsiniz. Uygulamanız özel izinler gerektiriyorsa, **özel** güvenlik bölgesini seçerek bunu yapabilirsiniz. Özel izinleri ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması Için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Bir güvenlik bölgesi ayarlamak için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Güvenlik** sekmesine tıklayın.  
  
3. **ClickOnce güvenlik ayarlarını etkinleştir** onay kutusunu seçin.  
  
4. **Bu bir kısmi güven uygulaması** seçenek düğmesini seçin.  
  
     **ClickOnce güvenlik izinleri** bölümündeki denetimler etkindir.  
  
5. **Uygulamanızın yükleneceği bölgede** , açılan listeden bir güvenlik bölgesi seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce uygulaması için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce Uygulamalarının Güvenliğini Sağlama](../deployment/securing-clickonce-applications.md)
