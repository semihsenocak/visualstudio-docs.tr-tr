---
title: Azure bulut hizmetlerinde hata ayıklama seçenekleri | Microsoft Docs
description: Azure bulut hizmetlerinde hata ayıklama
author: mikejo5000
manager: jillfra
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 94e7d48c767ef9705c20b049b57f459290679217
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911842"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Azure bulut hizmetinde hata ayıklamanın çeşitli yöntemlerini öğrenme
Bu makale, bir Azure bulut hizmetinde hata ayıklamanın çeşitli yollarına bağlantılar sağlar.

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Visual Studio 'da bir Azure bulut hizmetinde hata ayıklama
Azure işlem öykünücüsü 'nü kullanarak, yerel bir makinedeki bulut hizmetinizde hata ayıklaması yapmak için zaman ve para tasarrufu yapabilirsiniz. Dağıtmadan önce bir hizmette yerel olarak hata ayıkladığında, işlem süresi için ödeme yapmadan güvenilirliği ve performansı artırabilirsiniz. Ancak bazı hatalar yalnızca Azure 'da bir bulut hizmeti çalıştırdığınızda gerçekleşebilir. Yalnızca Azure 'da bir bulut hizmeti çalıştırdığınızda oluşan hatalar, hizmetinizi yayımladığınızda uzaktan hata ayıklamayı etkinleştirerek ve ardından hata ayıklayıcıyı bir rol örneğine iliştirerek hata ayıklanabilir. Daha fazla bilgi için bkz. [yerel bilgisayarınızda bulut hizmetinizde hata ayıklama](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>IntelliTrace’i kullanma
.NET Framework 4,5 hedeflenen rolleri yazmak için Visual Studio Enterprise kullanıyorsanız, Visual Studio 'dan bir Azure bulut hizmeti dağıtırken IntelliTrace 'i etkinleştirebilirsiniz. IntelliTrace, uygulamanızın Azure 'da çalışıyor gibi hatalarını ayıklamak için Visual Studio ile birlikte kullanabileceğiniz bir günlük sağlar. Daha fazla bilgi için bkz. [IntelliTrace ve Visual Studio ile yayımlanan bulut hizmetinde hata ayıklama](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

## <a name="remote-debugging"></a>Uzaktan hata ayıklama
Bulut hizmetini Visual Studio 'dan dağıtırken, bulut hizmetlerinize uzaktan hata ayıklamayı etkinleştirebilirsiniz. Bir dağıtım için uzaktan hata ayıklamayı etkinleştirmeyi seçerseniz, uzaktan hata ayıklama Hizmetleri her bir rol örneğini çalıştıran sanal makinelere yüklenir. Bu hizmetler-gibi `msvsmon.exe` -performansı etkilemez veya ek maliyetlerle sonuçlanır. Daha fazla bilgi için bkz. [Azure 'da bulut hizmetinde hata ayıklama](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio 'da bir Azure bulut hizmetinde veya VM 'de hata ayıklama](./vs-azure-tools-debug-cloud-services-virtual-machines.md) -Azure Cloud Services 'in nasıl ayıklanmasına ilişkin ayrıntıları öğrenin.
