---
title: Bir Çözümde Birden Çok DSL
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2eef29db24da3be0a9376ea76a9a1a551af9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542603"
---
# <a name="multiple-dsls-in-one-solution"></a>Bir Çözümde Birden Çok DSL

Birden çok DSLs 'yi tek bir çözümün parçası olarak paketleyebilir, böylece birlikte yüklenirler.

Birden çok DSLs 'yi bütünleştirmek için birkaç teknik kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio ModelBus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md) ve [nasıl yapılır: sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md) ve [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Aynı çözümde birden fazla DSL oluşturun

1. Yeni bir **VSIX proje** projesi oluşturun.

2. VSıX çözüm dizininde iki veya daha fazla DSL projesi oluşturun.

   - Her DSL için, Visual Studio 'nun yeni bir örneğini açın. Yeni DSL 'yi oluşturun ve VSıX çözümüyle aynı çözüm klasörünü belirtin.

   - Her bir DSL 'yi farklı bir dosya adı uzantısıyla oluşturduğunuzdan emin olun.

   - **DSL** ve **DslPackage** projelerinin adlarını farklı olacak şekilde değiştirin. Örneğin: `Dsl1` ,, `DslPackage1` `Dsl2` , `DslPackage2` .

   - Her **DslPackage \* \ Source.Extension.tt**içinde, bu satırı doğru DSL projesi adına güncelleştirin:

      `string dslProjectName = "Dsl2";`

   - VSıX çözümünde DSL * ve DslPackage \* projelerini ekleyin. Her çifti kendi çözüm klasörüne yerleştirmek isteyebilirsiniz.

2. DSLs 'lerin VSıX bildirimlerini birleştirin:

   1. _Yourvaltıproject_**\Source.Extension.manifest**açın.

   2. Her DSL için **Içerik Ekle** ve Ekle ' yi seçin:

       - `Dsl*`**MEF bileşeni** olarak proje

       - `DslPackage*`**MEF bileşeni** olarak proje

       - `DslPackage*`**vs paketi** olarak proje

3. Çözümü derleyin.

   Elde edilen VSıX her iki DSLs 'i de yükleyecek. F5 'i kullanarak bunları test edebilir veya _Yourvaltproject_**\Bin\Debug \\ \* . vsix**' yi dağıtabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)