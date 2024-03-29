---
title: 'CA1406: Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c20ea7bd7bba6f221395c7e2c21d6c1dcc241fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661290"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Özellikle bileşen nesne modeli (COM) tarafından görünür olarak işaretlenen bir tür, <xref:System.Int64?displayProperty=fullName> bağımsız değişkeni alan bir üye bildirir.

## <a name="rule-description"></a>Kural Tanımı
 Visual Basic 6 COM istemcisi 64-bit tamsayıya erişemez.

 Varsayılan olarak, aşağıdakiler COM 'a görünür: derlemeler, ortak türler, ortak türlerdeki ortak örnek üyeleri ve tüm ortak değer türleri üyeleri. Ancak, hatalı pozitif sonuçları azaltmak için bu kural, türün COM görünürlüğünü açık bir şekilde ifade etmek için gereklidir; kapsayan bütünleştirilmiş kod, <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> `false` ayarlanmış olarak işaretlenmelidir ve tür, <xref:System.Runtime.InteropServices.ComVisibleAttribute> `true` olarak işaretli olmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Değeri her zaman 32 bitlik bir integral olarak ifade edilebilir bir parametre için bu kural ihlalini onarmak için, parametre türünü <xref:System.Int32?displayProperty=fullName> olarak değiştirin. Parametrenin değeri 32 bitlik bir integral olarak ifade edilebileceğinden daha büyük olabilir, parametre türünü <xref:System.Decimal?displayProperty=fullName> olarak değiştirin. @No__t_0 ve <xref:System.Double?displayProperty=fullName> <xref:System.Int64> veri türünün üst aralıklarında duyarlık kaybı olduğunu unutmayın. Üyenin COM tarafından görülebilmesi amaçlıyoksa, <xref:System.Runtime.InteropServices.ComVisibleAttribute> ' ı `false` olarak ayarlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Visual Basic 6 COM istemcilerinin türe erişememesi durumunda, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: COM görünebilir türler içinde statik üyelerden kaçının](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen kod](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [uzun veri türüyle](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) birlikte çalışma
