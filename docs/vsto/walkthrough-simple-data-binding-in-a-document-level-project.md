---
title: 'İzlenecek yol: belge düzeyi projede basit veri bağlama'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c22947e572a29c2b49a5ce9bb808c3cf2fe2902
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584930"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>İzlenecek yol: belge düzeyi projede basit veri bağlama
  Bu izlenecek yol, belge düzeyindeki bir projede veri bağlamanın temellerini gösterir. SQL Server veritabanındaki tek bir veri alanı, Microsoft Office Excel içindeki bir adlandırılmış aralığa bağlanır. İzlenecek yol Ayrıca, tablodaki tüm kayıtlarda kaydırmanıza imkan tanıyan denetimlerin nasıl ekleneceğini gösterir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Excel projesi için veri kaynağı oluşturma.

- Çalışma sayfasına denetimler ekleme.

- Veritabanı kayıtları arasında gezinme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Northwind SQL Server örnek veritabanıyla bir sunucuya erişim.

- SQL Server veritabanına okuma ve yazma izinleri.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma
 Bu adımda, bir Excel çalışma kitabı projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Visual Basic veya C# kullanarak **basit veri bağlamamı**adlı bir Excel çalışma kitabı projesi oluşturun. **Yeni belge oluştur** ' un seçili olduğundan emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **basit veri bağlama projem** **Çözüm Gezgini**ekler.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma
 Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda, **View**  >  **diğer Windows**  >  **veri kaynaklarını**görüntüle ' yi seçerek bunu görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı**başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. Northwind örnek SQL Server veritabanına yönelik bir veri bağlantısı seçin veya **Yeni bağlantı** düğmesini kullanarak yeni bir bağlantı ekleyin.

5. Bir bağlantı seçildikten veya oluşturulduktan sonra **İleri**' ye tıklayın.

6. Seçildiğinde bağlantıyı kaydetme seçeneğini temizleyin ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesneleri** penceresinde **Tablolar** düğümünü genişletin.

8. **Müşteriler** tablosunun yanındaki onay kutusunu işaretleyin.

9. **Son**'a tıklayın.

   Sihirbaz, **müşteriler** tablosunu **veri kaynakları** penceresine ekler. Ayrıca, projenize **Çözüm Gezgini**görünür bir veri kümesi de ekler.

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Bu izlenecek yol için, ilk çalışma sayfasında iki adlandırılmış aralığa ve dört düğmeye ihtiyacınız vardır. İlk olarak, veri kaynağına otomatik olarak bağlanması için **veri kaynakları** penceresinden iki adlandırılmış aralığı ekleyin. Sonra, **araç kutusundan**düğmeleri ekleyin.

### <a name="to-add-two-named-ranges"></a>İki adlandırılmış aralık eklemek için

1. *My Simple Data Binding.xlsx* çalışma kitabının, **Sheet1** görüntülenirken Visual Studio tasarımcısında açık olduğunu doğrulayın.

2. **Veri kaynakları** penceresini açın ve **müşteriler** düğümünü genişletin.

3. **CompanyName** sütununu seçin ve ardından görüntülenen aşağı açılan oka tıklayın.

4. Açılan listede **NamedRange** ' i seçin ve ardından **CompanyName** sütununu **a1**hücresine sürükleyin.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>A1 hücresinde adlı bir denetim `companyNameNamedRange` oluşturulur. **A1** Aynı zamanda, <xref:System.Windows.Forms.BindingSource> adlandırılmış `customersBindingSource` , bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> projeye bir örnek eklenir. Denetim öğesine bağlanır <xref:System.Windows.Forms.BindingSource> , bu da <xref:System.Data.DataSet> örneğe bağlanır.

5. **Veri kaynakları** penceresinde **MüşteriNo** sütununu seçin ve ardından görüntülenen aşağı açılan oka tıklayın.

6. Açılan listede **NamedRange** ' e tıklayın ve sonra **CustomerID** sütununu **B1**hücresine sürükleyin.

7. Adlı başka bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Denetim `customerIDNamedRange` **B1**hücresinde oluşturulur ve öğesine bağlanır <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Dört düğme eklemek için

1. **Araç kutusunun** **ortak denetimler** sekmesinden, <xref:System.Windows.Forms.Button> çalışma sayfasının **a3** hücresine bir denetim ekleyin.

    Bu düğme adlandırılır `Button1` .

2. Adların gösterilmesi için, bu sırada aşağıdaki hücrelere üç tane daha düğme ekleyin:

   |Cep|(Ad)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   Sonraki adım düğmelere metin eklemek ve C# ' de olay işleyicileri eklemek olur.

## <a name="initialize-the-controls"></a>Denetimleri Başlat
 Olay sırasında düğme metnini ayarlayın ve olay işleyicileri ekleyin <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> .

### <a name="to-initialize-the-controls"></a>Denetimleri başlatmak için

1. **Çözüm Gezgini**, **Sheet1. vb** veya **Sheet1.cs**öğesine sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. Aşağıdaki kodu `Sheet1_Startup` yöntemine ekleyerek her düğme için metni ayarlayın.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. Yalnızca C# için, yöntemine düğme tıklama olayları için olay işleyicileri ekleyin `Sheet1_Startup` .

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   Şimdi, <xref:System.Windows.Forms.Control.Click> kullanıcıların kayıtlara göz atabilmesi için düğmelerin olaylarını işlemek üzere kod ekleyin.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Kayıtlar arasında kaydırmayı etkinleştirmek için kod ekleme
 <xref:System.Windows.Forms.Control.Click>Kayıtlar arasında gezinmek için her düğmenin olay işleyicisine kod ekleyin.

### <a name="to-move-to-the-first-record"></a>İlk kayda geçmek için

1. Düğmenin olayı için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `Button1` ve ilk kayda geçmek için aşağıdaki kodu ekleyin:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>Önceki kayda geçmek için

1. Düğmenin olayı için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `Button2` ve aşağıdaki kodu ekleyerek konumu bir arkaya taşıyın:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>Sonraki kayda geçmek için

1. Düğmenin olayı için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `Button3` ve aşağıdaki kodu ekleyerek konumu bir konuma ilerletin:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>Son kayda gitmek için

1. Düğmenin olayı için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `Button4` ve son kayda geçmek için aşağıdaki kodu ekleyin:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Uygulamayı test etme
 Artık çalışma kitabınızı test edebilir ve veritabanındaki kayıtlara göz atadığınızdan emin olun.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. İlk kaydın **a1** ve **B1**hücrelerinde göründüğünü onaylayın.

3. **>**( `Button3` ) Düğmesine tıklayın ve sonraki kaydın **a1** ve **B1**hücresinde göründüğünü onaylayın.

4. Kaydın beklendiği gibi değiştiği onaylamak için diğer kaydırma düğmelerine tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, adlandırılmış bir aralığı veritabanındaki bir alana bağlamanın temellerini gösterir. Daha sonra gelebilecek bazı görevler şunlardır:

- Çevrimdışı kullanılabilmesi için verileri önbelleğe alma. Daha fazla bilgi için bkz. [nasıl yapılır: çevrimdışı kullanım için verileri önbelleğe alma veya bir sunucu üzerinde](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Hücreleri tek bir alana değil, tablodaki birden çok sütuna bağlayın. Daha fazla bilgi için bkz. [Izlenecek yol: belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- <xref:System.Windows.Forms.BindingNavigator>Kayıtlar arasında gezinmek için bir denetim kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms BindingNavigator denetimi ile verilerde gezinme](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)
- [İzlenecek yol: belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
