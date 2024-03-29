---
title: 'CA1721: Özellik adları Get yöntemleriyle eşleşmemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 366932c83328c6810e0103308db1c73a3e3076cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671604"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Tür adları alma yöntemleriyle eşleşmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir üyenin adı ' Get ' ile başlar ve diğer bir deyişle ortak veya korumalı bir özelliğin adıyla eşleşir. Örneğin, ' GetColor ' adlı bir yöntemi ve ' Color ' adlı bir özelliği içeren bir tür bu kuralı ihlal ediyor.

## <a name="rule-description"></a>Kural Tanımı
 Get yöntemleri ve özellikleri, işlevini açıkça ayırt eden adlara sahip olmalıdır.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni bir yazılım kitaplığı öğrenmek için gereken süreyi azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Adı ' Get ' önekli bir yöntemin adıyla eşleşmemesi için değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

> [!NOTE]
> Bu uyarı, get yöntemi IExtenderProvider arabiriminin uygulanmasından kaynaklanıyorsa dışarıda bırakılmış olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir yöntem ve özellik içerir.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1024: Uygun yerlerde özellikler kullanın](../code-quality/ca1024-use-properties-where-appropriate.md)
