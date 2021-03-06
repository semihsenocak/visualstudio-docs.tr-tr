---
title: Office çözümlerinde uygulama ve dağıtım bildirimleri
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc4095ce8cd945ff35903c9d8ffc95400cc3b7ab
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584444"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Office çözümlerinde uygulama ve dağıtım bildirimleri
  Uygulama bildirimi, bir Office çözümü tarafından derlemelerini bulmak ve güncelleştirmek için kullanılan bilgileri sağlayan bir XML dosyasıdır. Uygulama bildirimi, uygulama bildirimi ve derlemelerinin en güncel sürümünü bulmak için gereken bilgileri sağlayan, sunucuda depolanan bir XML dosyası olan dağıtım bildirimiyle birlikte kullanılabilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Office çözümleri için bildirim yapısı
 Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan Microsoft Office çözümleri için tüm bildirimler standart ClickOnce şemasını temel alır. Office çözümlerinizi dağıttığınızda, hem belge düzeyi hem de VSTO eklentisi projelerine yönelik uygulama bildirimleri ClickOnce önbelleğinde bulunur. Dağıtım bildirimleri istemci bilgisayara kopyalanmaz.

 Office projelerine yönelik uygulama ve dağıtım bildirimlerinin içerikleri hakkında bilgi için bkz. Office çözümleri için [uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md) ve [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimleri oluşturma
 Uygulama bildirimleri, yapı sürecinin bir parçası olarak otomatik olarak oluşturulur. Belge düzeyinde bir proje oluşturduğunuzda, dağıtım bildiriminin konumu belgeye özel belge özelliği olarak katıştırılır. VSTO eklentileri için, dağıtım bildiriminin konumu kayıt defterinde saklanır.

 **Yayımlama Sihirbazı**hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Bildirimlerin Office çözümleriyle nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)