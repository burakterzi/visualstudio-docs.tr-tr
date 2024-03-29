---
title: 'CA2222: devralınan üye görünürlüğünü azaltma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3dda56e6980133b0e33893fbb814c4a3a7008c49
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656052"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Devralınan üye görünürlüğünü azaltmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Korumasız bir türdeki özel bir yöntem, bir temel tür içinde belirtilen ortak bir yöntemle aynı imzaya sahip. Özel yöntem son değil.

## <a name="rule-description"></a>Kural Tanımı
 Devralınan üyeler için erişim değiştiricisini değiştirmemelisiniz. Devralınmış bir üyeyi özel olarak değiştirme, arayanların yöntemin temel sınıf uygulamasına erişmesini engellemez. Üye özel hale getirilme ve tür korumasız ise, devralan türler, devralma hiyerarşisindeki metodun son ortak uygulamasını çağırabilir. Erişim değiştiricisini değiştirmeniz gerekiyorsa, yöntemin geçersiz olarak işaretlenmesi gerekir ya da yöntemin geçersiz kılınmasını engellemek için türünün mühürlü olması gerekir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için erişimi özel olmayan şekilde değiştirin. Alternatif olarak, programlama diliniz destekliyorsa, yöntemi son haline getirebilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
