---
title: Hata ayıklayıcıda bağlam işleci (C++) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: aa16bd6f93198e5360139dbc5a6a0d96f02a1e41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62564710"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Visual Studio hata ayıklayıcısında bağlam Işleci (C++)
Bir kesme noktası konumunu, değişken adını veya ifadeyi nitelemek için C++ ' daki bağlam işlecini kullanabilirsiniz. Bağlam işleci, başka bir şekilde yerel bir adla gizlenen bir dış kapsamdan bir ad belirtmek için yararlıdır.

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sözdizimi
 Bağlamını belirtmenin iki yolu vardır:

1. {,, [*module*]} *ifade*

     Küme ayraçları iki virgül ve modül (yürütülebilir veya DLL) adı veya tam yol içermelidir.

     Örneğin, EXAMPLE.dll işlevinde bir kesme noktası ayarlamak için `SomeFunction` :

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *Modül*! *ifade*

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *Modül* bir modülün adıdır. Aynı ada sahip modüller arasında belirsizliği ortadan kaldırmak için tam bir yol kullanabilirsiniz.

   *Modül* yolu virgül, gömülü bir boşluk veya küme ayracı içeriyorsa, bağlam ayrıştırıcısının dizeyi doğru bir şekilde tanıyabilmesi için yol etrafında tırnak işaretleri kullanmanız gerekir. Tek tırnak işaretleri Windows dosya adının bir parçası olarak değerlendirilir, bu nedenle çift tırnak işareti kullanmanız gerekir. Örneğin,

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *ifade* , bir işlev adı, değişken adı veya *modüldeki*işaretçi adresi gibi geçerli bir hedefe çözümlenen geçerli bir C++ ifadesiyse.

  İfade değerlendirici bir ifadede bir sembol ile karşılaştığında, sembolü aşağıdaki sırayla arar:

1. Güncel bloktan başlayarak, küme ayraçları içine alınmış deyimler dizisi ve kapsayan bloğa dışarıya devam eden sözcük temelli kapsam. Geçerli blok, geçerli konumu, yönerge işaretçisi adresini içeren koddur.

2. İşlev kapsamı. Geçerli işlev.

3. Geçerli konum bir C++ üye işlevi içindeyse sınıf kapsamı. Sınıf kapsamı tüm temel sınıfları içerir. İfade değerlendirici, normal baskınlık kurallarını kullanır.

4. Geçerli modüldeki genel semboller.

5. Geçerli programdaki ortak semboller.