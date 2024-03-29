---
title: 'CA1809: aşırı Yerellerden kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d23d9cc6006997c82451ac061e3ee0353e59b1b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671491"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Aşırı yerel öğelerden kaçın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir üye, biri derleyicinin ürettiği 64 taneden fazla yerel değişken içerir.

## <a name="rule-description"></a>Kural Tanımı
 Yaygın bir performans iyileştirmesi, değeri *kayıt* olarak adlandırılan bellek yerine işlemci kaydındaki bir değeri depolmedir. Ortak dil çalışma zamanı, kayıt için 64 yerel değişkene kadar kabul eder. Kayıtlı olmayan değişkenler yığına konur ve düzenlemeden önce bir kayda taşınması gerekir. Tüm yerel değişkenlerin kaydolma ihtimaline izin vermek için yerel değişken sayısını 64 olarak sınırlandırın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, uygulamayı 64 ' den fazla yerel değişken kullanmak üzere yeniden düzenleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek veya performans bir sorun değilse kuralı devre dışı bırakmak güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
