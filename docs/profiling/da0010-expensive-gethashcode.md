---
title: 'DA0010: pahalı GetHashCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9ce982c7a98fd12749c66c89e47bd895d2fb6a5d
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777692"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Pahalı GetHashCode

|||
|-|-|
|Kural Kimliği|DA0010|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemleri|Aşağıdakine<br /><br /> .NET belleği|
|İleti|GetHashCode işlevleri bir tek EAP olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse karma kod işlevinin karmaşıklığını azaltın.|
|İleti türü|Uyarı|

## <a name="cause"></a>Sebep
 Türün GetHashCode yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıyla veya yöntemin belleği ayırır.

## <a name="rule-description"></a>Kural açıklaması
 Karma, büyük bir koleksiyondaki belirli bir öğeyi hızlı bir şekilde bulmanın bir tekniğidir. Karma tabloları büyük olabileceğinden ve çok yüksek erişim fiyatlarını desteklemesi gerektiğinden, karma tabloların etkili olması gerekir. Bu gereksinimin bir engel, .NET Framework GetHashCode yöntemlerinin bellek ayırmamalıdır. Bellek ayırma, atık toplayıcıdaki yükü artırır ve ayırma isteğinin sonucu olarak çöp toplamayı çalıştırmak için gerekli hale gelirse, olası gecikmelerle yöntemi ortaya çıkarır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Metodun karmaşıklığını azaltın.
