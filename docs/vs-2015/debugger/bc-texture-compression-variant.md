---
title: BC doku sıkıştırma varyantı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f0758d9eb5a003b0353ceb4fee21996d90685fa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161696"
---
# <a name="bc-texture-compression-variant"></a>BC Doku Sıkıştırma Çeşidi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

B8G8R8X8, B8G8R8A8 veya R8G8B8A8 çeşitlemesi olan bir piksel biçimi olan dokuların blok sıkıştırmasını sunar.  
  
## <a name="interpretation"></a>Yorumlama  
 BC1, BC2 ve BC3 gibi blok tabanlı sıkıştırma biçimleri, sıkıştırılmamış görüntü biçimlerinden önemli ölçüde daha az bellek kaplar ve bu nedenle önemli ölçüde daha az bellek bant genişliği tüketir. Piksel başına 32 bit kullanan sıkıştırılmamış bir biçime kıyasla, BC1 (eski adıyla DXT1) 8:1 Compression ve BC3 (eski adıyla, daha önce DXT5 olarak bilinirdi) 4:1. BC1 ve BC3 arasındaki fark BC1 bir alfa kanalını desteklemekte olsa da, BC3 blok ile sıkıştırılmış bir alfa kanalını destekler. Yüksek sıkıştırma oranlarına rağmen, tipik dokuların görüntü kalitesinde yalnızca küçük bir azalma vardır. Bununla birlikte, belirli dokuların (örneğin, küçük bir alanda önemli renk çeşitlemelerine sahip olanlar) sıkıştırılması, kabul edilemez sonuçlara neden olabilir.  
  
 Dokularınız blok tabanlı sıkıştırma için uygun ise ve kusursuz renge uygunluk gerekmiyorsa, bellek kullanımını azaltmak ve daha az bant genişliği kullanmak için blok ile sıkıştırılmış bir biçim kullanmayı düşünün.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kaynak dokusu oluşturan her çağrıda bir blok tabanlı sıkıştırma biçimi kullanarak dokuları sıkıştırın `ID3DDevice::CreateTexture2D` . Özellikle, dokular şu durumlarda sıkıştırılır:  
  
- `D3D11_TEXTURE2D_DESC`Geçirilen nesne, değişmeyen `pDesc` bir gölgelendirici kaynağını açıklar; bu:  
  
  - BindFlags üyesi yalnızca D3D11_BIND_SHADER_RESOURCE bayrak kümesine sahiptir.  
  
  - Kullanım üyesi D3D11_USAGE_DEFAULT ya da D3D11_USAGE_IMMUTABLE olarak ayarlanır.  
  
  - CPUAccessFlags üyesi 0 olarak ayarlanır (CPU erişimi yok).  
  
  - SamplerDesc üyesinin Count üyesi 1 olarak ayarlanmış (çok örnekli bir kenar yumuşatma (MSAA)).  
  
- Çağrısına ilk veriler verilir `CreateTexture2D` .  
  
  Desteklenen kaynak biçimleri ve blok sıkıştırılmış biçimleri aşağıda verilmiştir.  
  
|Özgün biçim (başlangıç)|Sıkıştırılmış biçim (için)|  
|------------------------------|------------------------------|  
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (eski adıyla DXT1)|  
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|  
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|  
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (eski adıyla DXT5)|  
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|  
  
 Dokuınızın listede bulunmayan bir biçimi varsa doku değiştirilmez.  
  
## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar  
 Bazen B8G8R8A8 veya R8G8B8A8 görüntü biçimlerinin bir çeşitlemesi ile oluşturulan dokular, gerçekte alfa kanalını kullanmaz, ancak değişkenin kullanılıp kullanılmadığını bilmeleri için bir yol yoktur. Alfa kanalının kullanıldığı durumda, değişken her zaman bu biçimleri daha az etkin BC3 biçimine kodluyor. Bu değişkenle, değişkenin daha verimli BC1 biçimini kullanabilmesi için alfa kanalını kullanmadığınız durumlarda B8G8R8X8 görüntü biçiminin bir varyasyonunu kullanarak, uygulamanızın olası işleme performansını daha iyi anlamanıza yardımcı olabilirsiniz Grafik Çerçeve Çözümlemesi.  
  
## <a name="example"></a>Örnek  
 Bu değişken bloğu-, çağrısından önce çalışma zamanında dokuları sıkıştırır `CreateTexture2D` . Sıkıştırılmamış dokular daha fazla disk alanı kullandığından ve blok tabanlı sıkıştırma için önemli işlem kaynakları kodlamak gerektiğinden, ek adım uygulamanızdaki yükleme sürelerini önemli ölçüde artırabildiğinden üretim kodu için bu yaklaşıma önerilir. Bunun yerine, yapı işlem hattınızın bir parçası olan bir görüntü Düzenleyicisi veya görüntü işlemcisi kullanarak dokularınızı çevrimdışına sıkıştırmanız önerilir. Bu yaklaşımlar, disk alanı gereksinimlerini azaltır, uygulamanızdaki çalışma zamanı ek yükünü ortadan kaldırır ve en iyi görüntü kalitesini sürdürebilmeniz için daha fazla işleme süresine sahiptir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yarı/çeyrek doku boyutları varyantı](../debugger/half-quarter-texture-dimensions-variant.md)
