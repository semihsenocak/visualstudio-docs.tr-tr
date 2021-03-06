---
title: 'İzlenecek yol: başlangıç sayfasına özel XAML ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674121"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>İzlenecek Yol: Başlangıç Sayfasına Özel XAML Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir Web tarayıcısı içeren özel bir Visual Studio başlangıç sayfası oluşturmayı gösterir.  
  
## <a name="adding-custom-xaml"></a>Özel XAML ekleme  
  
1. [Özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md)yönergelerini Izleyerek bir başlangıç sayfası oluşturun.  
  
2. MainWindow. xaml dosyasında \<Grid> bölümünü bulun.  
  
3. \<TabControl> \<TabItem> \< Grid> Aşağıdaki örnekte gösterildiği gibi bir öğesi ve öğesi içine ekleyin.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. \<TabItem>Yeni bir proje açan bir öğe ile ikinci bir ekleyin \<Button> :  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Özel başlangıç sayfasını test etme  
  
1. F5 tuşuna basın.  
  
     Visual Studio 'nun deneysel örneği, özel başlangıç sayfası yüklenmiş ancak seçilmemiş olarak açılır.  
  
2. Visual Studio 'nun deneysel örneğinde **Araçlar/Seçenekler/ortam** sayfasını açın.  
  
3. **Başlatma**' yı seçin. **Başlangıç sayfası Özelleştir** listesinde,. xaml dosyanızı seçin ve **Tamam**' a tıklayın.  
  
4. **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.  
  
5. **Bing** sekmesine tıklayın.  
  
     Bing Web sayfası görmeniz gerekir.  
  
6. **MyButton** sekmesine tıklayın.  
  
     **Yeni proje** iletişim kutusunu açan bir **MyProject** düğmesi görmeniz gerekir.  
  
7. Deneysel örneği kapatın.  
  
## <a name="applying-the-custom-start-page"></a>Özel başlangıç sayfası uygulanıyor  
  
#### <a name="to-test-the-custom-start-page"></a>Özel başlangıç sayfasını test etmek için  
  
1. **Araçlar/Seçenekler/ortamda** **Başlangıç**' ı seçin. **Başlangıç sayfası Özelleştir** listesinde,. xaml dosyanızı seçin ve **Tamam**' a tıklayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Visual Studio başlangıç sayfasında artık bir Web tarayıcısı sekmesi ve MyButton sekmesi görüntülenen bir sekme bulunur. [Başlangıç sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)bölümünde gösterildiği *gibi, özel* bir. dll eklemek için başka IŞLEVLERE sahip özel başlangıç sayfaları oluşturabilirsiniz. Elde edilen. vsix dosyasını [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine veya başka bir Web sitesi ya da ağ paylaşımında yayımlayarak, özel başlangıç sayfalarını diğer kullanıcılarla paylaşabilirsiniz. Daha fazla bilgi için bkz. [özel başlangıç sayfaları dağıtma](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF kapsayıcı denetimleri](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
