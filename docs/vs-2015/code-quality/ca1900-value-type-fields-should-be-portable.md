---
title: 'CA1900: değer türü alanları taşınabilir olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff56c89a56af54288284d9cc62c71d0c9b2179b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661100"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Değer tür alanları taşınabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1900: değer türü alanları taşınabilir](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable)olmalıdır.

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategori|Microsoft. taşınabilirlik|
|Yeni Değişiklik|Parçalama-alan, derleme dışında görünebilirler.<br /><br /> Bölünmez olmayan-alan, derleme dışında görünür değilse.|

## <a name="cause"></a>Sebep
 Bu kural, 64 bit işletim sistemlerinde yönetilmeyen koda kopyalandıklarında açık düzen ile belirtilen yapıların doğru şekilde hizalanmasını denetler. IA-64 hizalanmamış bellek erişimine izin vermez ve bu ihlalin düzeltilmediğinde işlem kilitlenir.

## <a name="rule-description"></a>Kural Tanımı
 Yanlış hizalanmış alanlar içeren açık düzene sahip yapılar 64 bitlik işletim sistemlerinde kilitlenmelere neden olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 8 bayttan küçük olan tüm alanlar, boyutunun birden çok katı olan uzaklıklara sahip olmalıdır ve 8 bayt ya da daha fazla alan, 8 ' in katı olan uzaklıklara sahip olmalıdır. Farklı bir çözüm ise, `LayoutKind.Explicit` yerine `LayoutKind.Sequential` kullanmaktır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarı yalnızca hatada gerçekleşirse bastırılmalıdır.
