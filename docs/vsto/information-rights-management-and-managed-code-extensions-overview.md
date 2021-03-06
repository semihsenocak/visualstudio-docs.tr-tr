---
title: Yönetilen kod uzantıları & bilgi hakları yönetimi
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 753f3d2da201c67cd86c697eccf7580596a40d6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68872057"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış
  Microsoft Office Word ve Microsoft Office Excel, yetkisiz kişilerin hassas bilgileri görüntülemesini veya değiştirmesini önlemeye yardımcı olabilecek bilgiler Rights Management (ıRM) sağlar. Bilgilerin nasıl çalıştığı hakkında daha fazla Rights Management bilgi için, bkz. belirli Office uygulamasındaki Yardım.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Kısıtlı izinlerle arka planda kod Çalıştır
 Çözümünüz ıRM kullanan bir belge veya çalışma kitabı içeriyorsa, varsayılan olarak Word ve Excel hiçbir kodun çalışmasına izin vermez. Belgenin yazarından veya tam denetim erişimine sahipseniz, çözümünüzün çalışması için varsayılan olarak değişiklik yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 IRM, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> belgesinde önbelleğe alınan verileri almak veya işlemek için kullanımını engeller.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Son kullanıcılar yönetilen kod uzantıları kullanan belgelerle ilgili izinleri kısıtlar
 Çözümünüzde belge veya çalışma kitabına tam denetim erişimi olan herkes, izinleri kısıtlamak için ıRM kullanabilir. Örneğin, muhasebe departmanındaki bir son kullanıcı bir çalışma sayfasını bir veritabanından alınan verilerle otomatik olarak dolduran bir çözüm kullanıyorsa, bu kullanıcı yalnızca departmandaki kişilere ve başkalarına okuma erişimine izin vermek isteyebilir. Kullanıcı kısıtlı izinleri eklediğinde, varsayılan olarak, çalışma sayfasının arkasındaki kod çalıştırılamaz ve çalışma sayfası verilerle doldurulmaz.

 Sorunu gidermek için, belgeye veya çalışma kitabına tam denetim erişimi olan birinin, nesne modeline programlı erişim sağlamak için varsayılan izin ayarlarını değiştirmesi gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerinde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
