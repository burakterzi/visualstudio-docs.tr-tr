---
title: 'CA2243: öznitelik dize sabit değerleri doğru ayrıştırılmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 62a2adc6f01e5cb26a6af26d71a124f8b81e07fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671970"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Öznitelik dize harfleri doğru çözümlenmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Özniteliğin dize sabit değeri bir URL, GUID veya sürüm için doğru ayrıştırılmadı.

## <a name="rule-description"></a>Kural Tanımı
 Öznitelikleri <xref:System.Attribute?displayProperty=fullName> ' dan türetildiğinden ve öznitelikler derleme zamanında kullanıldığından, kurucularına yalnızca sabit değerler geçirilebilir. URL 'Leri, GUID 'Leri ve sürümleri temsil etmesi gereken öznitelik parametreleri <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> ve <xref:System.Version?displayProperty=fullName> olarak yazılamıyor, çünkü bu türler sabitler olarak gösterilemez. Bunun yerine, dizeler tarafından temsil etmelidir.

 Parametresi bir dize olarak yazıldığı için, derleme zamanında hatalı biçimlendirilmiş bir parametrenin geçirilmesi mümkündür.

 Bu kural bir Tekdüzen Kaynak tanımlayıcısı (URI), genel olarak benzersiz tanımlayıcı (GUID) veya sürüm temsil eden parametreleri bulmak için bir adlandırma buluşsal yöntemi kullanır ve geçilen değerin doğru olduğunu doğrular.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Parametre dizesini doğru biçimlendirilmiş bir URL, GUID veya sürüm olarak değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Parametresi bir URL, GUID veya sürüm temsil etmediği takdirde bu kuraldan bir uyarının bastırmasının güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden AssemblyFileVersionAttribute için kodu gösterir.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Kural, aşağıdakiler tarafından tetiklenir:

- ' Version ' içeren ve System. Version olarak ayrıştırılabilecek parametreler.

- ' Guid ' içeren ve System. Guid olarak ayrıştırılabilen parametreler.

- ' Uri ', ' urn ' veya ' URL ' içeren parametreler, System. Uri olarak ayrıştırılamıyor.

## <a name="see-also"></a>Ayrıca Bkz.
 [CA1054: URI parametreleri dizeler olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
