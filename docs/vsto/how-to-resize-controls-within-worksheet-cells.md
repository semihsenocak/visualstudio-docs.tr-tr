---
title: 'Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2d22973e13ee77b66de303041f8b6a765b4b93a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545879"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma
  Çalışma sayfasındaki sütunları veya satırları yeniden boyutlandırdığınızda, hücrelerdeki tüm konak denetimleri yeniden boyutlandırıldı hücrenin Yükseklik veya genişliğine otomatik olarak yeniden boyutlandırılır. Windows Forms denetimleri varsayılan olarak otomatik olarak yeniden boyutlandırılır.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Denetimleri tasarım zamanında eklerseniz, her denetim için konumlandırma seçeneklerini ayarlamanız gerekir.

 Programlı olarak bir Windows Forms denetimi ekler ve bir Aralık bağımsız değişkeni sağlarsanız, Aralık içindeki bir hücre yeniden boyutlandırılırken denetim otomatik olarak yeniden boyutlandırılır. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Tasarım zamanında denetimleri yeniden boyutlandırma

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Denetimlerin tasarım zamanında hücrelerle yeniden boyutlandırılmasını sağlamak için

1. **Araç kutusundan**bir Windows Forms denetimini çalışma sayfasına sürükleyin.

2. Denetime sağ tıklayın ve sonra **Biçim denetimi**' ne tıklayın.

3. **Biçim denetimi** Iletişim kutusunda **Özellikler** sekmesine tıklayın.

4. **Nesne konumlandırma**altında, **Hücrelerle taşı ve Boyutlandır** seçeneğini belirleyin ve ardından **Tamam**' a tıklayın.

     Denetimi içeren hücreyi yeniden boyutlandırdığınızda, denetim hücreye sığacak şekilde yeniden boyutlandırılır.

## <a name="resize-controls-at-run-time"></a>Çalışma zamanında denetimleri yeniden boyutlandırma
 Çalışma zamanında bir Windows Forms denetimi ekler ve <xref:Microsoft.Office.Interop.Excel.Range> denetimin konumu olarak bir olarak geçirirseniz, aralığı içeren çalışma sayfası hücresi yeniden boyutlandırılırken denetim otomatik olarak yeniden boyutlandırılır.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Denetimlerin çalışma zamanında hücrelerle yeniden boyutlandırılması için

1. A1 aralığına bir denetim ekleyin.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Denetimi içeren hücreyi yeniden boyutlandırdığınızda, denetim hücreye sığacak şekilde yeniden boyutlandırılır.

## <a name="reset-control-placement"></a>Denetim yerleşimini Sıfırla
 `Placement`Özelliği aşağıdaki değerlerden birine ayarlayarak denetimin yerleşimini ve yeniden boyutlandırılmasını sıfırlayabilirsiniz <xref:Microsoft.Office.Interop.Excel.XlPlacement> :

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Bir denetimin davranışını yeniden boyutlandırmaması veya hücreyle birlikte hareket ettirmek üzere değiştirmek için

1. Denetimin yerleşim özelliğini çağırın ve değerini olarak ayarlayın <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Nasıl yapılır: yazdırırken çalışma sayfalarında denetimleri gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
