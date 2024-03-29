---
title: 'CA1026: varsayılan parametreler kullanılmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8fffbdc2cf9f4e09fe98c8e14b6692802ab3f275
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661952"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Varsayılan parametreler kullanılmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir tür, varsayılan bir parametre kullanan dışarıdan görünür bir yöntem içerir.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan parametreleri kullanan yöntemlere ortak dil belirtimi (CLS) altında izin verilir; Ancak, CLS, derleyicilerin bu parametrelere atanan değerleri yoksaymasına olanak tanır. Varsayılan parametre değerlerini yoksayması gereken derleyiciler için yazılan kod, her varsayılan parametre için açıkça bağımsız değişken sağlamalıdır. Programlama dilleri arasında istediğiniz davranışı sürdürmek için, varsayılan parametreleri kullanan yöntemlerin varsayılan parametreleri sağlayan yöntem aşırı yüklemeleri ile değiştirilmelidir.

 Derleyici, yönetilen koda eriştiğinde yönetilen uzantının C++ varsayılan parametrelerinin değerlerini yoksayar. Visual Basic Derleyicisi, [Isteğe bağlı](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) anahtar sözcüğünü kullanan Varsayılan parametrelere sahip yöntemleri destekler.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için varsayılan parametreleri kullanan yöntemi varsayılan parametreleri sağlayan yöntem aşırı yüklemeleri ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, varsayılan parametreleri kullanan bir yöntemi ve eşdeğer işlevselliği sağlayan aşırı yüklenmiş yöntemleri gösterir.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1025: Tekrarlanan bağımsız değişkenleri params dizisi ile değiştirin](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
