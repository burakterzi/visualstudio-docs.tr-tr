---
title: 'DA0013: yüksek dize. Split veya String. SUBSTRING kullanımı | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d42469ac5236a41eda96af5d1fe896a5ed84a321
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779419"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Yüksek oranda String.Split veya String.Substring kullanımı

|||
|-|-|
|Kural Kimliği|DA0013|
|Kategori|.NET Framework Kullanım Kılavuzu|
|Profil oluşturma yöntemleri|Aşağıdakine|
|İleti|String. Split ve String. SUBSTRING işlevlerinin kullanımını azaltmayı göz önünde bulundurun.|
|Kural türü|Uyarı|

## <a name="cause"></a>Sebep
 System. String. Split veya System. String. Substring yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir bölümüdür. Bir dizedeki alt dizenin varlığını test ediyorsanız System. String. IndexOf veya System. String. IndexOfAny kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Split yöntemi bir dize nesnesi üzerinde çalışır ve özgün dizenin alt dizelerini tutan yeni bir dize dizisi döndürür. İşlevi döndürülen dizi nesnesi için bellek ayırır ve bulduğu her dizi öğesi için yeni bir dize nesnesi ayırır. Benzer şekilde, substr Yöntemi bir String nesnesi üzerinde çalışır ve istenen alt dizeyle eşdeğer olan yeni bir dize döndürür.

 Uygulamanızda bellek ayırmaları yönetimi önemliyse, String. Split ve String. substr yöntemlerine alternatifleri kullanmayı göz önünde bulundurun. Örneğin, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanabilirsiniz.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Örnekleme profili verilerinin [Işlev ayrıntıları görünümüne](../profiling/function-details-view.md) gitmek için **hata listesi** penceresindeki iletiye çift tıklayın. System. String. Split veya System. String. substr yöntemlerinin en sık kullanımını yapan programın bölümlerini bulmak için çağırma işlevlerini inceleyin. Mümkünse, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanın.
