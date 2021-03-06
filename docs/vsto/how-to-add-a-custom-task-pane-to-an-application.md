---
title: 'Nasıl yapılır: uygulamaya özel görev bölmesi ekleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0df4d51795f01c98790f1d5b0525c45cc71899ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546217"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Nasıl yapılır: uygulamaya özel görev bölmesi ekleme
  VSTO eklentisini kullanarak yukarıda listelenen uygulamalara özel bir görev bölmesi ekleyebilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Uygulamaya özel görev bölmesi ekleme

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Uygulamaya özel görev bölmesi eklemek için

1. Yukarıda listelenen uygulamalardan biri için bir VSTO eklenti projesi açın veya oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Proje** menüsünde **Kullanıcı denetimi Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** iletişim kutusunda, Yeni Kullanıcı denetiminin adını **MyUserControl**olarak değiştirin ve ardından **Ekle**' ye tıklayın.

     Kullanıcı denetimi tasarımcıda açılır.

4. **Araç kutusundan** bir veya daha fazla Windows Forms denetimini Kullanıcı denetimine ekleyin.

5. **ThisAddIn.cs** veya **ThisAddIn. vb** kod dosyasını açın.

6. Sınıfına aşağıdaki kodu ekleyin `ThisAddIn` . Bu kod `MyUserControl` <xref:Microsoft.Office.Tools.CustomTaskPane> , sınıfının üyeleri olarak ve örneklerini bildirir `ThisAddIn` .

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. Olay işleyicisine aşağıdaki kodu ekleyin `ThisAddIn_Startup` . Bu kod, <xref:Microsoft.Office.Tools.CustomTaskPane> nesneyi koleksiyona ekleyerek yeni bir oluşturur `MyUserControl` `CustomTaskPanes` . Kod ayrıca görev bölmesini de görüntüler.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > Bu kod, özel görev bölmenizi uygulamadaki etkin pencere ile ilişkilendirir. Bazı uygulamalarda, görev bölmesinin uygulamadaki diğer belge veya öğelerle göründüğünden emin olmak için bu kodu değiştirmek isteyebilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
