---
title: İfade değerlendirici mimarisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8e0aa8f5cc45e0f6e012ecb3f0a27a22725a259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805634"
---
# <a name="expression-evaluator-architecture"></a>İfade Değerlendirici Mimarisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Özel bir dili Visual Studio hata ayıklama paketiyle tümleştirmek, gerekli ifade değerlendirici (EE) arabirimlerini uygulama ve ortak dil çalışma zamanı sembol sağlayıcısı (SP) ve Ciltçi arabirimlerini çağırma anlamına gelir. SP ve Ciltçi nesneleri, geçerli yürütme adresiyle birlikte, ifadelerin değerlendirildiği bağlamıdır. Bu arabirimlerin ürettiği ve tükettiği bilgiler, bir EE mimarisinde temel kavramları temsil eder.  
  
## <a name="overview"></a>Genel Bakış  
  
### <a name="parsing-the-expression"></a>Ifadeyi ayrıştırma  
 Bir programda hata ayıklarken, ifadeler bir dizi nedenden dolayı değerlendirilir, ancak hata ayıklamakta olan program bir kesme noktasında durdurulduğunda (Kullanıcı tarafından ya da bir özel durum nedeniyle oluşan bir kesme noktası). Visual Studio, [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabirimi tarafından temsil edilen bir yığın ÇERÇEVESINI (de) hata ayıklama altyapısından (de) aldığında şu anda. Daha sonra Visual Studio [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini almak Için [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) öğesini çağırır. Bu arabirim, ifadelerin değerlendirileceği bağlamı temsil eder; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , değerlendirme işleminin giriş noktasıdır. Bu noktaya kadar tüm arabirimler DE tarafından uygulanır.  
  
 `IDebugExpressionContext2::ParseText`Çağrıldığında,, kesme noktasının gerçekleştiği kaynak dosyanın diliyle ILIŞKILI Ee 'ı başlatır (Ayrıca, bu noktada sh 'i de başlatır). EE, [ıdebugexpressiondeğerlendirici](../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabirimi tarafından temsil edilir. Ardından, ifadeyi (metin biçiminde) Ayrıştırılacak bir ifadeye dönüştürmek için [ayrıştırmayı](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağırır. Bu ayrıştırılmış ifade [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimi tarafından temsil edilir. İfadenin genellikle ayrıştırılıp bu noktada değerlendirilmediğini unutmayın.  
  
 DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimini uygulayan bir nesne oluşturur, nesnesini `IDebugParsedExpression` nesnesine koyar `IDebugExpression2` ve `IDebugExpression2` öğesinden nesnesini döndürür `IDebugExpressionContext2::ParseText` .  
  
### <a name="evaluating-the-expression"></a>Ifade değerlendiriliyor  
 Visual Studio, ayrıştırılmış ifadeyi değerlendirmek için [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ya da [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) öğesini çağırır. Bu yöntemlerin her ikisi de [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , `IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` ayrıştırılmış ifadeyi değerlendirmek ve ayrıştırılmış ifadenin değerini ve türünü temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürmek için EvaluateSync öğesini çağırır (yöntemi hemen, bir arka plan iş parçacığı aracılığıyla çağırır). `IDebugParsedExpression::EvaluateSync` , ayrıştırılmış ifadeyi arabirim tarafından temsil edilen gerçek bir değere dönüştürmek için sağlanan SH, Address ve Ciltçi 'yi kullanır `IDebugProperty2` .  
  
### <a name="for-example"></a>Örneğin  
 Çalışan bir programda bir kesme noktasına isabet ettikten sonra, Kullanıcı **hızlı izleme** iletişim kutusunda bir değişken görüntülemeyi seçer. Bu iletişim kutusu değişkenin adını, değerini ve türünü gösterir. Kullanıcı genellikle değeri değiştirebilir.  
  
 **QuickWatch** iletişim kutusu gösterildiğinde, incelenmekte olan değişkenin adı, [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)'e metin olarak gönderilir. Bu, ayrıştırılmış ifadeyi temsil eden bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi döndürür, bu durumda değişkeni. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) daha sonra `IDebugProperty2` değişkenin değerini ve türünü ve adını temsil eden bir nesne oluşturmak için çağrılır. Bu bilgiler görüntülenir.  
  
 Kullanıcı değişkenin değerini değiştirirse, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) yeni değerle çağrılır ve bu nedenle, program çalışmaya devam ettiğinde kullanılacak.  
  
 Değişkenlerin değerlerini görüntüleme işlemi hakkında daha fazla ayrıntı için bkz. [Locals görüntüleme](../../extensibility/debugger/displaying-locals.md) . Bir değişkenin değerinin nasıl değiştirildiği hakkında daha fazla ayrıntı için bkz. [yerel öğenin değerini değiştirme](../../extensibility/debugger/changing-the-value-of-a-local.md) .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Değerlendirme Bağlamı](../../extensibility/debugger/evaluation-context.md)  
 , EE çağrısı yaparken geçirilen bağımsız değişkenleri sağlar.  
  
 [Anahtar İfade Değerlendiricisi Arabirimleri](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Bir EE yazarken, değerlendirme bağlamı ile birlikte gereken önemli arabirimleri açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR Ifade Değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)   
 [Yerel Bir Öğenin Değerini Değiştirme](../../extensibility/debugger/changing-the-value-of-a-local.md)
