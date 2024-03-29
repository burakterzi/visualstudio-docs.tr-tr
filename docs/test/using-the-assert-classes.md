---
title: MSTest onaylama sınıfları ve yöntemleri
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 41be3aaa4967e4c5f975b43f7d8fec982f04c9b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659729"
---
# <a name="use-assert-classes-for-unit-testing"></a>Birim testi için onaylama sınıfları kullanma

Belirli işlevleri doğrulamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting> ad alanının onaylama sınıflarını kullanın. Bir birim testi yöntemi uygulamanızın kodundaki bir yöntemin kodunu, ancak onay deyimleri dahil ederseniz kodun davranışının doğruluğunu bildirir.

## <a name="kinds-of-asserts"></a>Onay türleri

@No__t_0 ad alanı çeşitli tür onaylama sınıfları sağlar.

Test yönteminizdeki <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> gibi <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> sınıfın herhangi bir yöntemini çağırabilirsiniz. @No__t_0 sınıfı, aralarından seçim yapabileceğiniz birçok yöntem içerir ve çoğu yöntemin birçok aşırı yüklemesi vardır.

### <a name="compare-strings-and-collections"></a>Dizeleri ve koleksiyonları karşılaştırın

Nesne koleksiyonlarını karşılaştırmak veya bir koleksiyonun durumunu doğrulamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> sınıfını kullanın.

Dizeleri karşılaştırmak ve incelemek için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> sınıfını kullanın. Bu sınıf <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> ve <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType> gibi çeşitli yararlı yöntemler içerir.

### <a name="exceptions"></a>Özel Durumlar

@No__t_0 özel durumu bir test başarısız olduğunda oluşturulur. Test zaman aşımına uğrarsa başarısız olur, beklenmeyen bir özel durum oluşturur veya **başarısız** bir sonuç üreten bir onay açıklaması içerir.

@No__t_0 bir test, **Sonuçlandırılamayan**bir sonuç üretdiğinde oluşturulur. Genellikle, hala çalıştırılmakta olduğunu göstermek için, üzerinde çalışmakta olduğunuz teste bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> ifadesini eklersiniz.

> [!NOTE]
> Alternatif bir strateji, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> özniteliğiyle çalıştırılmaya hazırlanmayan bir testi işaretlemenize olanak sağlar. Ancak, bu, uygulanmayan testlerin sayısı üzerinde kolayca rapor oluşturmamalarınızın dezavantajı vardır.

Yeni bir onay özel durum sınıfı yazarsanız, özel durumu test veya üretim kodunuzda oluşan beklenmeyen bir özel durum yerine bir onaylama hatası olarak belirlemeyi kolaylaştırmak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> taban sınıftan alın.

Uygulama kodunuzda bir yöntem tarafından oluşturulması beklenen bir özel durumun gerçekten oluşturulmuş olduğunu doğrulamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)