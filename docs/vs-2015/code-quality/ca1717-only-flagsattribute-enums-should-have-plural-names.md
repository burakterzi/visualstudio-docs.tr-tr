---
title: 'CA1717: Yalnızca FlagsAttribute numaralandırmalarında çoğul adlar olmalıdır. | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff67145d2a5e52e1ef6a803bde2468d1ec8528b3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630893"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Yalnızca FlagsAttribute numaralandırmalarında çoğul adlar olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda en son sürümünü şu yolda bulunabilir: [CA1717: yalnızca FlagsAttribute numaralandırmalarında çoğul adlar olmalıdır](https://docs.microsoft.com/visualstudio/code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names).  
  
TypeName | OnlyFlagsEnumsShouldHavePluralNames |  
| Checkıd | CA1717 |  
| Kategori | Microsoft.Naming|  
| Yeni değişiklik | Bozucu |  
  
## <a name="cause"></a>Sebep  
 Dışarıdan görünen bir sabit listesi adı çoğul Word'de sona erer ve numaralandırma ile işaretlenmemiş <xref:System.FlagsAttribute?displayProperty=fullName> özniteliği.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Adlandırma kuralları numaralandırma için adlandırma aynı anda birden fazla numaralandırma değeri belirtilebilir gösterir. <xref:System.FlagsAttribute> Derleyiciler sabit numaralandırma üzerinde bit düzeyinde işlemler sağlayan bir bit alanı olarak değerlendirilmesi gerektiğini söyler.  
  
 Bir kerede tek bir numaralandırma değeri belirtilebilir yalnızca, sabit listesi adı tekil bir sözcük olmalıdır. Örneğin, Haftanın günlerinin ingilizceleridir tanımlayan bir numaralandırma kullanılmak üzere bir uygulama birden çok gün belirleyebileceğiniz ayarlanmış olabilir. Bu numaralandırma olmalıdır <xref:System.FlagsAttribute> ve 'Gün' çağrılabilir. Belirtilecek yalnızca tek bir günde izin veren benzer bir sabit listesi özniteliğine sahip değil ve olabilir 'Day' denir.  
  
 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıkları için genel bir bakış sağlar. Bu, yeni bir yazılım kitaplığı öğrenmek için gereklidir ve kitaplık geliştirme yönetilen kodda uzmanlığına sahip olan kişi tarafından geliştirilmiştir müşterilerinizin size olan güvenini artırır süreyi azaltır.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Sabit listesi adı tekil bir sözcük yapın veya ekleme <xref:System.FlagsAttribute>.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Tekil bir sözcük adı sona ererse kuraldan bir uyarıyı bastırmak güvenlidir.  
  
## <a name="related-rules"></a>İlgili kuralları  
 [CA1714: Bayrak numaralandırmalarında çoğul adlar olmalıdır](../code-quality/ca1714-flags-enums-should-have-plural-names.md)  
  
 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Sabit Listesi Tasarımı](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)


