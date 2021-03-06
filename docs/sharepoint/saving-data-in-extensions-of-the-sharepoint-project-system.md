---
title: SharePoint proje sisteminin uzantılarında veri kaydetme | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30142b9aaec3df7ce0d43845e369eb538533de62
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583872"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>SharePoint proje sisteminin uzantılarında veri kaydetme
  SharePoint proje sistemini genişlettiğinizde, bir SharePoint projesi kapatıldıktan sonra devam eden dize verilerini kaydedebilirsiniz. Veriler genellikle belirli bir proje öğesiyle veya projenin kendisiyle ilişkilendirilir.

 Kalıcı hale getirilmesi gerekmeyen verileriniz varsa, bu verileri, arabirimi uygulayan SharePoint araçları nesne modelinde herhangi bir nesneye ekleyebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> . Daha fazla bilgi için bkz. [SharePoint Araçları uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Bir proje öğesiyle ilişkili verileri kaydetme
 Bir proje öğesine eklediğiniz bir özelliğin değeri gibi belirli bir SharePoint proje öğesiyle ilişkili verileriniz varsa, verileri proje öğesi için *. spdata* dosyasına kaydedebilirsiniz. Bunu yapmak için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> bir nesnenin özelliğini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> . Bu özelliğe eklediğiniz veriler, proje öğesi için *. spdata* dosyasındaki **ExtensionData** öğesine kaydedilir. Daha fazla bilgi için bkz. [ExtensionData öğesi](../sharepoint/extensiondata-element.md).

 Aşağıdaki kod örneği, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> özel bir SharePoint proje öğesi türünde tanımlanan bir dize özelliğinin değerini kaydetmek için özelliğinin nasıl kullanılacağını gösterir. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Bir projeyle ilişkili verileri kaydetme
 SharePoint projelerine eklediğiniz bir özelliğin değeri gibi proje düzeyi verileriniz varsa, verileri proje dosyasına ( *. csproj* dosyası veya *. vbproj* dosyası) veya proje Kullanıcı seçenek dosyasına ( *. csproj. User* dosyası veya *. vbproj. User* dosyası) kaydedebilirsiniz. Verileri kaydetmek için seçtiğiniz dosya, verilerin nasıl kullanılmasını istediğinize bağlıdır:

- Verilerin SharePoint projesini açan tüm geliştiriciler tarafından kullanılabilmesini istiyorsanız, verileri proje dosyasına kaydedin. Bu dosya her zaman kaynak denetim veritabanlarına iade edilir, bu nedenle bu dosyadaki veriler projeyi kullanıma alan diğer geliştiriciler tarafından kullanılabilir.

- Verilerin yalnızca SharePoint projesini Visual Studio 'da açık olan güncel geliştirici için kullanılabilir olmasını istiyorsanız, verileri proje Kullanıcı seçenek dosyasına kaydedin. Bu dosya genellikle kaynak denetimi veritabanlarına iade edilmez, bu nedenle bu dosyadaki veriler projeyi kullanıma alan diğer geliştiriciler için kullanılamaz.

### <a name="save-data-to-the-project-file"></a>Verileri proje dosyasına kaydet
 Proje dosyasına verileri kaydetmek için bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesneyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> nesnesine dönüştürün ve sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> yöntemini kullanın. Aşağıdaki kod örneğinde bir proje özelliğinin değerini proje dosyasına kaydetmek için bu yöntemin nasıl kullanılacağı gösterilmektedir. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>Nesneleri Visual Studio Otomasyon nesne modeli veya Tümleştirme nesne modelindeki diğer türlere dönüştürme hakkında daha fazla bilgi için bkz. [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Verileri proje Kullanıcı seçenek dosyasına kaydet
 Proje Kullanıcı seçenek dosyasına veri kaydetmek için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> bir nesnenin özelliğini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> . Aşağıdaki kod örneğinde, proje özelliğinin değerini proje Kullanıcı seçenek dosyasına kaydetmek için bu özelliğin nasıl kullanılacağı gösterilmektedir. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [SharePoint Araç Uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
