---
title: 'CA2239: isteğe bağlı alanlar için seri durumdan çıkarma yöntemleri sağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5604b697af1716e918f3a0f6d9a26ddbe70fc0b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672964"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür, <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş ve tür serileştirme olay işleme yöntemleri sağlamayan bir alana sahiptir.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 özniteliğinin serileştirme üzerinde hiçbir etkisi yoktur; özniteliği ile işaretlenmiş bir alan serileştirilir. Ancak, alanı seri hale getirme sırasında yok sayılır ve kendi türüyle ilişkili varsayılan değeri korur. Seri hale getirme işlemi sırasında alanı ayarlamak için de serileştirme olay işleyicileri bildirilmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, türe serileştirme olay işleme yöntemleri ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Seri hale getirme işlemi sırasında alanın yoksayılması gerekiyorsa, bu kuraldan bir uyarıyı gizlemek güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, isteğe bağlı bir alan ve Serileştirme olay işleme yöntemleri içeren bir türü gösterir.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
