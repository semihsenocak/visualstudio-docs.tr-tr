---
title: devinit komutları
description: Bileşenleri yüklemek için devinit komutlarının nasıl kullanılacağına ilişkin ayrıntılar.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: a22e0f5a20050e62aa9978c40f2189c82ca3071c
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352329"
---
# <a name="devinit-commands"></a>devinit komutları

## <a name="init"></a>Init

```console
> devinit init
```

Geçerli çalışma dizinindeki [_.devinit.js_](devinit-json.md) dosyasında belirtilen araçları çalıştırarak ortamı başlatın.  

### <a name="options-for-init"></a>İnit seçenekleri

Komut için isteğe bağlı seçenekler `devinit init` .

| Bağımsız Değişken             | Gerekli | Açıklama                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--dosyası           | No       | Dosyadaki _.devinit.js_ yolu.                                         |
| --hata-eylem       | No       | Hataların nasıl işleneceğini belirtir. Seçenekler: durdur, Yoksay, devam et (varsayılan).|
| -v,--verbose         | No       | Ayrıntılı çıktıyı yay.                                                      |
| -n,--Kuru çalıştırma         | No       | Kuru çalıştırma.                                                                  |

## <a name="run"></a>Çalıştır

```console
> devinit run -t <toolname>
```

Belirli aracı çalıştırır, parametreler aşağıda listelenmiştir. Belirli kullanımlar için her bir araç için [belgelere](devinit-tool-list.md) bakın.

### <a name="options-for-run"></a>Çalıştırma seçenekleri

Komut için Seçenekler `devinit run` .

| Bağımsız Değişken                                  | Gerekli | Açıklama                                                                          |
|-------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--aracı                                 | Yes      | Gereklidir. Araç adı.                                                             |
| -ı,--girişi                                | No       | Araç giriş değeri. Örneğin, bir dosya adı, paket veya ad.                           |
| --hata-eylem                            | No       | Araç hatalarının nasıl işleneceğini belirtir: durdur, Yoksay, devam et. Varsayılan değer durdurulur. |
| -v,--verbose                              | No       | Ayrıntılı çıktıyı yay.                                                                 |
| -n,--Kuru çalıştırma                              | No       | Kuru çalıştırma.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; &lt; argN&gt;  | No       | Araca ek komut satırı bağımsız değişkenleri.                                       |

#### <a name="--file-argument"></a>--Dosya bağımsız değişkeni

Dosyadaki _devinit.jsyolunu belirtir. – File belirtilmemişse, aşağıdaki konumlarda varsayılan bir dosya aradık:

* {geçerli-dizin} \\ Üzerinde.devinit.js
* {geçerli-dizin} \\ . devinit \\.devinit.json

`.`Dizinde veya dosya adında önünde olmayan yollar da eşleşmeyecektir.

#### <a name="--error-action-argument"></a>--hata-eylem bağımsız değişkeni

Bir araç sıfır olmayan bir çıkış kodu döndürürse gerçekleştirilecek eylemi belirtir. Geçerli değerler şunlardır:

| Bağımsız Değişken | Description                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Standart hataya bir hata gönderdikten sonra diğer araçları işlemeye devam edin. devinit.exe çıkış kodu sıfır değil (hata). Bu davranış durdurma hatası eylemine benzerdir, ancak işleme devam eder. `continue` init komutu için varsayılan hata-eylem.              |
| yoksayma   | Standart çıktıya bir uyarı yaydıktan sonra diğer araçları işlemeye devam edin. DevInit işlem çıkış kodu her zaman sıfır (başarılı) olmalıdır. `ignore`Ayar tüm hataları yoksayar.                                                                                                      |
| Dur     | Standart hataya bir hata yayar ve araçları işlemeyi durduruyor. devinit.exe çıkış kodu sıfır değil (hata). Bu, devam etme hatası eylemine benzerdir, ancak karşılaşılan ilk hatada işleme durdurulur. `stop` , init hariç tüm komutlar için varsayılan hata eylemi olur. |

#### <a name="--dry-run-switch"></a>--Kuru çalıştırma anahtarı

Çalıştırılacak, ancak herhangi bir araç yürütmeyin yankı araç komutları. 

#### <a name="--verbose-switch"></a>--ayrıntılı anahtar

Ayrıntılı çıktıyı standart çıktıya yay. Yürütülecek araç ayrıntılı bir seçeneği destekliyorsa, ayrıntılı anahtarı araca yayın.

#### <a name="additional-command-line-arguments"></a>Ek komut satırı bağımsız değişkenleri

Değerinde bir boşluk içeren bir kullanmak, başka bir kaçış `<arg>` tırnak çifti içermelidir.

```console
> devinit run -t <toolname> -<somearg> "<some value>"
```

Belirli bir dizine DotNet yüklemek için `C:\Program Files\dotnet` :

```console
> devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>Liste

```console
> devinit list
```

Tüm kullanılabilir araçların listesini yazdırır.

## <a name="show"></a>Göster

```console
> devinit show -t <toolname>
```

| Bağımsız Değişken       | Gerekli | Açıklama                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--aracı      | Yes      | Gereklidir. Araç adı.                                                             |

Belirli bir araç için yardım bilgilerini yazdırır.

## <a name="version"></a>Sürüm

```console
> devinit version
```

Devinit için geçerli sürüm bilgilerini yazdırır.

## <a name="help"></a>Yardım

```console
> devinit help
> devinit help list
```

Devinit veya belirli bir komut için yardım metnini yazdırır `devinit <command>` .
 