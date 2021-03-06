---
title: IDiaTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b9c9f85ffbf4eed2fdc305a64bd3f32822dacd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682785"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir DIA veri kaynağı tablosunu numaralandırır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaTable` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Bu Numaralandırıcının [IEnumVARIANT arabirimi](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) sürümünü alır.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Tablonun adını alır.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Tablodaki öğelerin sayısını alır.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Belirli bir giriş dizinine bir başvuru alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, `IEnumUnknown` Microsoft. VisualStudio. OLE. Interop ad alanındaki Enumeration yöntemlerini uygular. `IEnumUnknown`Sabit listesi arabirimi, [IDiaTable:: Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) ve [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) metotlarından daha fazla tablo içeriğine yineleme yapmak için çok daha etkilidir.  
  
 `IUnknown` `IDiaTable::Item` Yönteminden ya da `Next` yönteminden (Microsoft. VisualStudio. OLE. Interop ad alanında) döndürülen arabirimin yorumu, tablo türüne bağlıdır. Örneğin, `IDiaTable` arabirim eklenen kaynakların bir listesini temsil ediyorsa, `IUnknown` [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) arabirimi için arabirim sorgulanmalıdır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) veya [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) yöntemlerini çağırarak bu arabirimi elde edin.  
  
 Aşağıdaki arabirimler `IDiaTable` arabirimiyle uygulanır (yani, `IDiaTable` arabirimi aşağıdaki arabirimlerden biri için sorgulayabilirsiniz):  
  
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Örnek  
 İlk işlev, `ShowTableNames` oturumdaki tüm tabloların adlarını görüntüler. İkinci işlevi, `GetTable` belirtilen bir arabirimi uygulayan bir tablo için tüm tabloları arar. Üçüncü işlevi, `UseTable` işlevinin nasıl kullanılacağını gösterir `GetTable` .  
  
> [!NOTE]
> `CDiaBSTR` , `BSTR` örnekleme kapsam dışına geçtiğinde bir ve otomatik olarak dizeyi serbest bırakma olarak işleyen bir sınıftır.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: dia2. h  
  
 Kitaplık: diaguid. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (hata ayıklama arabirimi erişim SDK 'Sı)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
