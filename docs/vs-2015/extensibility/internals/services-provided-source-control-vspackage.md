---
title: Sunulan hizmetler (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 750710cdc381573f8aa6fd064e1fc980030cf359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202702"
---
# <a name="services-provided-source-control-vspackage"></a>Sağlanan Hizmetler (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hizmetler, işlevin VSPackages arasında ve Visual Studio tümleşik geliştirme ortamı (IDE) ile yüklü VSPackages 'ler arasında paylaşıldığı birincil mekanizmadır. Hizmetlerin ayrıntılı açıklaması ve Visual Studio IDE 'deki önem derecesi için bkz.[Hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Kaynak denetim hizmeti  
 Visual Studio, iki katmanlı hizmet, IDE düzeyi hizmet ve paket düzeyi hizmet sunar. Visual Studio IDE yerel olarak IDE düzeyi hizmetler sağlar. Kaynak denetim paketi bu hizmetlerden bazılarını tüketir. Kaynak denetim paketi VSPackage, kendi kendine özel bir kaynak denetimi hizmeti sağlayarak kaynak denetimi işlevselliğini paylaşır. Kaynak denetim paketi, Visual Studio IDE tarafından kullanılabilecek bir sözleşme biçiminde uygulanan kaynak denetimi ile ilgili arabirimlerin kümesini kapsüller.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
