---
title: Abonelikler yönetim portalındaki atamaları silme | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 09/21/2020
ms.topic: how-to
description: Yöneticilerin Visual Studio abonelikleri yönetim portalındaki abonelik atamalarını nasıl silebileceğinizi öğrenin
ms.openlocfilehash: 0ce0235d75946f46d39c78084121ce295067d74e
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022274"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Visual Studio aboneliklerinde atamaları silme
Bir abone artık şirketten ayrıldıklarında, bir projeyi tamamlamada veya yeni bir iş rolüne geçiş yaparken olduğu gibi bir Visual Studio aboneliği gerektirdiğinde, aboneliğini kaldırabilir ve başka birine atayabilirsiniz. Aboneliği yeniden atadığınızda, tüm abone avantajlarının sıfırlanmadığını lütfen unutmayın.  Yeni Kullanıcı, talep edilmemiş anahtarları talep edebilir ve daha önce **talep edilen anahtarları görüntüleyebilir, ancak** talep limitleri sıfırlanmaz.  Kurumsal anlaşmalar (EA) olan kuruluşlar için, özgün kullanıcı tarafından kullanılan Pluralaltim eğitimi gibi tüm avantajlar sıfırlanır. 

Atamaları silme hakkında bilgi edinmek için bu videoyu izleyin veya okumaya devam edin.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Abonelik atamasını silme
1. Kaldırmak istediğiniz abonenin adına tıklayın. Kaldırmak üzere birden çok abone seçmek için, abone adının solundaki daireye tıklayarak her birini seçebilirsiniz.  Alternatif olarak, **CTRL** tuşunu basılı tutarak kaldırmak istediğiniz her aboneye tıklayabilirsiniz. Bir dizi aboneyi kaldırmak için, ilk birine tıklayın, **SHIFT** tuşuna basın ve son ' a tıklayın.  Tüm aboneleri seçmek ve kaldırmak için **CTRL + A** tuşlarına basın. Bu örnekte, üç adet aboneler, Kai ve Madison-silinir. 
2. Seçili aboneyi silmek için **Sil**' e tıklayın.
3. İletiyi silme işlemini onaylamanızı isteyen göründüğünde **Tamam**' a tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Aboneleri Sil](_img/delete-license/delete-subscribers.png "Silmek istediğiniz kullanıcıları seçin ve Sil ' e tıklayın. Birden çok aboneyi seçmek için CTRL ve Shift tuşlarını kullanabilirsiniz.")

   > [!NOTE]
   > Şablon kullanılarak toplu silme kullanılamıyor. Azure Active Directory güvenlik grupları aracılığıyla abonelik atamalarını yöneten kuruluşlar için, silme işlemlerinin nasıl gerçekleştiği hakkında daha fazla bilgi için [makalemize](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) bakın.  

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Bir aboneliğin silinmesine gerek kalmadan değiştirilsin mi?  [Abonelikleri nasıl düzenleyeceğinizi](edit-license.md) öğrenin
- Belirli bir aboneliği bulma konusunda yardım için [bir abonelik aramaya](search-license.md)göz atın.
- Aboneliklerinizin bir listesini oluşturmanız mı gerekiyor?  Lütfen [abonelikleri dışarı aktarma](exporting-subscriptions.md)bölümüne bakın.