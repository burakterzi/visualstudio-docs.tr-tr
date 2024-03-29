---
title: 'CA2103: kesinlik güvenliği gözden geçirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b4abf0b15a4fbba1abc61572da8a2f6126c754f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652153"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Kesinlik temelli güvenliği gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir yöntem zorunlu güvenliği kullanır ve durum bilgileri veya dönüş değerlerini kullanarak izin oluşturursa, izin talebi etkin durumdayken değişebilir.

## <a name="rule-description"></a>Kural Tanımı
 Zorunlu güvenlik, kod yürütme sırasında izinleri ve güvenlik eylemlerini belirtmek için yönetilen nesneleri kullanır ve meta verilerde izinleri ve eylemleri depolamak için öznitelikler kullanır. Zorunlu güvenlik, bir izin nesnesinin durumunu ayarlayabilmeniz ve çalışma zamanına kadar kullanılamayan bilgileri kullanarak güvenlik eylemleri seçeceğinden çok esnektir. Bu esneklikle birlikte, bir iznin durumunu belirlemede kullandığınız çalışma zamanı bilgilerinin, eylem yürürlükte olduğu sürece değişmeden kalmayacağı riski vardır.

 Bildirime dayanan güvenliği mümkün olduğunca kullanın. Bildirim temelli taleplerin anlaşılması daha kolay.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İzin durumunun kullanıldığı sürece değişebilir bilgilere dayanmadığından emin olmak için, zorunlu güvenlik taleplerini gözden geçirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İzin değişen verilere bağlı değilse, bu kuraldan bir uyarı bastırması güvenlidir. Ancak, zorunlu talebin bildirime dayalı eşdeğerini değiştirmek daha iyidir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
