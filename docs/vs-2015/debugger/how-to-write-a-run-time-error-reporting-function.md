---
title: 'Nasıl yapılır: çalışma zamanı hata raporlama Işlevi yazma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6468e14e3ed588386440e992d9a570e735123bab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65678901"
---
# <a name="how-to-write-a-run-time-error-reporting-function"></a>Nasıl Yapılır: Çalışma Zamanı Hata Raporlama İşlevi Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalışma zamanı hataları için özel bir raporlama işlevi, ile aynı bildirime sahip olmalıdır `_CrtDbgReportW` . Hata ayıklayıcıya 1 değerini döndürmelidir.  
  
 Aşağıdaki örnek, bir özel raporlama işlevinin nasıl tanımlanacağını göstermektedir.  
  
## <a name="example"></a>Örnek  
  
```  
#include <stdio.h>  
int errorhandler = 0;  
void configureMyErrorFunc(int i)  
{  
    errorhandler = i;  
}  
  
int MyErrorFunc(int errorType, const wchar_t *filename,  
                int linenumber, const wchar_t *moduleName,  
                const wchar_t *format, ...)  
{  
    switch (errorhandler)  
    {  
    case 0:  
    case 1:  
        wprintf(L"Error type %d at %s line %d in %s",  
                errorType, filename, linenumber, moduleName);  
        break;  
    case 2:  
    case 3:  
        fprintf(stderr, "Error type");  
        break;  
    }  
  
    return 1;  
}  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, daha karmaşık bir özel raporlama işlevi gösterilmektedir. Bu örnekte, Switch ifadesinde parametresi tarafından tanımlandığı şekilde çeşitli hata türleri ele alır `reportType` `_CrtDbgReportW` . Değiştirdiğiniz için `_CrtDbgReportW` kullanamazsınız `_CrtSetReportMode` . İşleviniz çıktıyı işlemelidir. Bu işlevdeki ilk değişken bağımsız değişkeni bir çalışma zamanı hata numarası alır. Daha fazla bilgi için bkz. [_RTC_SetErrorType](https://msdn.microsoft.com/library/f5f99be7-d357-4b11-b8f5-ddd3428f2b06).  
  
```  
#include <windows.h>  
#include <stdarg.h>  
#include <rtcapi.h>  
#include <malloc.h>  
#pragma runtime_checks("", off)  
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,   
                   const wchar_t *module, const wchar_t *format, ...)  
{  
    // Prevent re-entrance.  
    static long running = 0;  
    while (InterlockedExchange(&running, 1))  
        Sleep(0);  
    // Now, disable all RTC failures.  
    int numErrors = _RTC_NumErrors();  
    int *errors=(int*)_alloca(numErrors);  
    for (int i = 0; i < numErrors; i++)  
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);  
  
   // First, get the rtc error number from the var-arg list.  
    va_list vl;  
    va_start(vl, format);  
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);  
    va_end(vl);  
  
    wchar_t buf[512];  
    const char *err = _RTC_GetErrDesc(rtc_errnum);  
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",  
        err,  
        line,  
        file ? file : L"Unknown",  
        module ? module : L"Unknown");  
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;  
    // Now, restore the RTC errortypes.  
    for(int i = 0; i < numErrors; i++)  
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);  
    running = 0;  
    return res;  
}  
#pragma runtime_checks("", restore)  
```  
  
## <a name="example"></a>Örnek  
 Yerine `_RTC_SetErrorFuncW` özel işlevinizi yüklemek için kullanın `_CrtDbgReportW` . Daha fazla bilgi için bkz. [_RTC_SetErrorFuncW](https://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a). `_RTC_SetErrorFuncW`Dönüş değeri, bir önceki raporlama işlevidir ve gerekirse bunları kaydedebilir ve geri yükleyebilirsiniz.  
  
```  
#include <rtcapi.h>  
int main()  
{  
    _RTC_error_fnW oldfunction, newfunc;  
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);  
    // Run some code.  
    newfunc = _RTC_SetErrorFuncW(oldfunction);  
    // newfunc == &MyErrorFunc;  
    // Run some more code.  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Çalışma Zamanı Denetimlerini Özelleştirme](../debugger/native-run-time-checks-customization.md)
