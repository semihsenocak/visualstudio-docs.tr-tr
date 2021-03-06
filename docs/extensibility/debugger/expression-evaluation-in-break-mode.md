---
title: Kesme modunda ifade değerlendirmesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738726"
---
# <a name="expression-evaluation-in-break-mode"></a>Kesme modunda ifade değerlendirmesi
Aşağıdaki bölümde, hata ayıklayıcı kesme modundayken ve ifade değerlendirmesi yapmak gerektiğinde oluşan işlem açıklanmaktadır.

## <a name="expression-evaluation-process"></a>İfade değerlendirme işlemi
 Aşağıda, bir ifadeyi değerlendirmek için temel adımlar verilmiştir:

1. Oturum hata ayıklama Yöneticisi (SDM), [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) öğesini çağırarak bir ifade bağlamı arabirimi alır, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. SDM daha sonra [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) öğesini ayrıştırılacak dizeyle çağırır.

3. ParseText S_OK döndürmezse, hatanın nedeni döndürülür.

     güvenmiyorsanız

     ParseText S_OK döndürmezse, SDM, ayrıştırılmış ifadeden son bir değer elde etmek için [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ya da [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) öğesini çağırabilir.

    - Kullanırken `IDebugExpression2::EvaluateSync` , belirtilen geri çağırma arabirimi değerlendirmenin devam eden işlemine iletişim kurar. Son değer bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabiriminde döndürülür.

    - Kullanırken `IDebugExpression2::EvaluateAsync` , belirtilen geri çağırma arabirimi değerlendirmenin devam eden işlemine iletişim kurar. Değerlendirme tamamlandıktan sonra, EvaluateAsync geri çağırma aracılığıyla bir [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimi gönderir. Bu olay arabirimiyle, son değer [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)ile sonuçlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
