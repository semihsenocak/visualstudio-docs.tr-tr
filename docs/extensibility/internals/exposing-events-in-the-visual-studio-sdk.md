---
title: Visual Studio SDK 'da olayları gösterme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708483"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Visual Studio SDK 'da olayları kullanıma sunma
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Otomasyonu kullanarak olayları kaynak yapmanızı sağlar. Projeler ve proje öğeleri için olayları kaynak yapmanızı öneririz.

 Olaylar, Otomasyon tüketicileri tarafından <xref:EnvDTE.DTEClass.Events%2A> nesnesinden veya <xref:EnvDTE.DTEClass.GetObject%2A> (örneğin, `GetObject("EventObjectName")` ) alınır. Ortam `IDispatch::Invoke` , `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` bir olayı döndürmek için veya bayraklarını kullanarak çağırır.

 Aşağıdaki işlem, VSPackage 'a özgü olayların nasıl döndürüleceğini açıklar.

1. Ortam başlatılır.

2. Tüm VSPackages 'in **Otomasyon**, **AutomationEvents**ve **AutomationProperties** anahtarlarının altındaki tüm değer adlarını kayıt defterinden okur ve bu adları bir tabloda depolar.

3. Otomasyon tüketicisi, bu örnekte veya ' de çağırır `DTE.Events.AutomationProjectsEvents` `DTE.Events.AutomationProjectItemsEvents` .

4. Ortam, tablodaki dize parametresini bulur ve karşılık gelen VSPackage 'ı yükler.

5. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> çağrıya geçirilen adı kullanarak yöntemini çağırır; Bu örnekte `AutomationProjectsEvents` veya `AutomationProjectItemsEvents` .

6. VSPackage, ve gibi yöntemlere sahip bir kök nesnesi oluşturur `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` ve ardından nesneye bir IDispatch işaretçisi döndürür.

7. Ortam, Otomasyon çağrısına geçirilen ada göre uygun yöntemi çağırır.

8. `get_`Yöntemi, hem arabirimini hem de `IConnectionPointContainer` arabirimini uygulayan `IConnectionPoint` ve nesnesine döndüren başka bir IDispatch tabanlı olay nesnesi oluşturur `IDispatchpointer` .

   Otomasyonu kullanarak bir olayı göstermek için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> kayıt defterine eklediğiniz dizeleri yanıtlamanız ve bunları izlemeniz gerekir. Temel proje örneğinde dizeler *BscProjectsEvents* ve *BscProjectItemsEvents*' dir.

## <a name="registry-entries-from-the-basic-project-sample"></a>Temel proje örneğindeki kayıt defteri girişleri
 Bu bölümde, kayıt defterine Otomasyon olay değerlerinin ekleneceği yer gösterilmektedir.

 **[HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0\Packages \\<PkgGUID \> \Automationevents]**

 **AutomationProjectEvents** = nesnesini döndürür `AutomationProjectEvents` .

 **AutomationProjectItemEvents** = nesnesini döndürür `AutomationProjectItemsEvents` .

|Ad|Tür|Aralık|Description|
|----------|----------|-----------|-----------------|
|Varsayılan (@)|REG_SZ|Kullanılmıyor|Kullanılmıyor. Belgeler için veri alanını kullanabilirsiniz.|
|*AutomationProjectsEvents*|REG_SZ|Olay nesnenizin adı.|Yalnızca anahtar adı ilgili. Belgeler için veri alanını kullanabilirsiniz.<br /><br /> Bu örnek, temel proje örneğinden gelir.|
|*AutomationProjectItemEvents*|REG_SZ|Olay nesnenizin adı|Yalnızca anahtar adı ilgili. Belgeler için veri alanını kullanabilirsiniz.<br /><br /> Bu örnek, temel proje örneğinden gelir.|

 Olay nesnelerinizin herhangi biri bir Otomasyon tüketicisi tarafından istendiğinde, VSPackage 'ın desteklediği herhangi bir olay için yöntemler içeren bir kök nesnesi oluşturun. Ortam, `get_` Bu nesne üzerinde uygun yöntemi çağırır. Örneğin, çağrılırsa, `DTE.Events.AutomationProjectsEvents` `get_AutomationProjectsEvents` kök nesnesindeki yöntem çağrılır.

 ![Visual Studio proje olayları](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Olaylar için otomasyon modeli

 Sınıfı `CProjectEventsContainer` *BscProjectsEvents*için kaynak nesnesini temsil eder ve `CProjectItemsEventsContainer` *BscProjectItemsEvents*için kaynak nesnesini temsil eder.

 Çoğu durumda, çoğu olay nesnesi bir filtre nesnesi alıp, her olay isteği için yeni bir nesne döndürmelidir. Olaylarınızı ateşleyerek, olay işleyicisinin çağrıldığından emin olmak için bu filtreyi kontrol edin.

 *AutomationEvents. h* ve *AutomationEvents. cpp* aşağıdaki tablodaki sınıfların bildirimlerini ve uygulamalarını içerir.

|Sınıf|Açıklama|
|-----------|-----------------|
|`CAutomationEvents`|Nesnesinden alınan bir olay kök nesnesi uygular `DTE.Events` .|
|`CProjectsEventsContainer` ve `CProjectItemsEventsContainer`|Karşılık gelen olayları harekete alan olay kaynağı nesnelerini uygulayın.|

 Aşağıdaki kod örneği bir olay nesnesi için bir isteğin nasıl yanıtlanacağını göstermektedir.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 Yukarıdaki kodda, ( `g_wszAutomationProjects` *FigProjects*figprojectsevents) proje koleksiyonunuzun adı ve `g_wszAutomationProjectsEvents` *FigProjectsEvents* `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*), VSPackage uygulamanızdan kaynaklaştırılmış proje olayları ve proje öğeleri olaylarının adlarıdır.

 Olay nesneleri aynı merkezi konumdan alınır, `DTE.Events` nesnesi. Bu şekilde, bir son kullanıcının belirli bir olayı bulmak için tüm nesne modeline gözatmasına sahip olmaması için tüm olay nesneleri birlikte gruplandırılır. Bu Ayrıca, sistem genelinde olaylar için kendi kodunuzu uygulamanızı gerektirmek yerine, belirli VSPackage nesnelerinizi sağlamanıza olanak tanır. Bununla birlikte, arabiriminiz için bir olay bulması gereken son kullanıcı için, `ProjectItem` olay nesnesinin alındığı yerden hemen net değildir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
