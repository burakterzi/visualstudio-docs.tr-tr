---
title: 'CA2238: serileştirme yöntemlerini doğru uygulayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57e735db68d90130b537f9f5f4b220bd688c7675
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666679"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Serileştirme yöntemlerini doğru uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA2238: serileştirme yöntemlerini doğru uygulama](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Parçalama-Yöntem derleme dışında görünüyorsa.<br /><br /> Kırılmamış-Yöntem, derleme dışında görünür değilse.|

## <a name="cause"></a>Sebep
 Seri hale getirme olayı tanıtan yöntem türü, doğru imzaya, dönüş türüne veya görünürlüğe sahip değil.

## <a name="rule-description"></a>Kural Tanımı
 Bir yönteme aşağıdaki serileştirme olay özniteliklerinden birini uygulayarak bir serileştirme olay işleyicisi atanır:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Serileştirme olay işleyicileri <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> türünde tek bir parametre alır, `void` döndürür ve `private` görünürlüğe sahiptir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için, serileştirme olay işleyicisinin imzasını, dönüş türünü veya görünürlüğünü düzeltin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte doğru şekilde belirtilen serileştirme olay işleyicileri gösterilmektedir.

 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
