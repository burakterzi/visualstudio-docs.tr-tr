---
title: 'CA2151: kritik türler içeren alanlar güvenlik açısından kritik olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5dee78ef3c487541363e9e290e54a8f3d68cf3b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667423"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: Kritik türler içeren alanlar güvenlik açısından kritik olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Güvenlik saydam alanı veya güvenli kritik alanı bildirilir. Türü güvenlik açısından kritik olarak belirtilir. Örneğin:

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

 Bu örnekte `m_field`, güvenlik açısından kritik olan bir türün güvenlik saydam alanıdır.

## <a name="rule-description"></a>Kural Tanımı
 Kritik güvenlik türlerini kullanmak için türe başvuran kod güvenliği kritik veya güvenlik güvenli kritik olmalıdır. Dolaylı başvuru olsa bile bu doğrudur. Örneğin, kritik bir türü olan saydam alana başvuru yaptığınızda, kodunuz güvenlik açısından kritik veya güvenlik güvenli olmalıdır. Bu nedenle, bir güvenlik saydam veya güvenlik güvenli kritik alana erişmek mümkün olmayacaktır, çünkü saydam kod hala alana erişemeyecektir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için alanı <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyin ya da alan ETH güvenliği saydam veya güvenli kritik tarafından başvurulan türü oluşturun.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Açıklamalar
