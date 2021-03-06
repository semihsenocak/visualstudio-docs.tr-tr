---
title: İşaretçilerimin bellek adresini bozup bozmadığını bul | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 075569815d55ea30f688c5ce86c56990fca03cd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350361"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Kendi İşaretçilerimin Bellek Adresini Bozup Bozmadığını Nasıl Anlarım?
## <a name="problem-description"></a>Sorun Açıklaması
 İşaretçilerimin bir birinin 0x00408000 adresindeki belleği bozuyor olabileceğini düşünüyorum. Ne olduğunu öğrenmek için ne olduğunu nasıl anlarım?

## <a name="solution"></a>Çözüm

#### <a name="check-for-heap-corruption"></a>Yığın bozulmasını denetle

- Çoğu bellek bozulması aslında yığın bozulması nedeniyle olur. Genel Bayraklar yardımcı programını (gflags.exe) veya pageheap.exe kullanmayı deneyin. Bkz. [/Windows-Hardware/Drivers/Debugger/Gflags-and-PageHeap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Bellek adresinin değiştirildiğini bulmak için

1. 0x00408000 konumunda bir veri kesme noktası ayarlayın. Bkz. [veri değişikliği kesme noktası ayarlama (yalnızca yerel C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Kesme noktasına ulaştığınızda, 0x00408000 ' dan başlayan bellek içeriğini görüntülemek için **bellek** penceresini kullanın. Daha fazla bilgi için bkz. [bellek pencereleri](../debugger/memory-windows.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
