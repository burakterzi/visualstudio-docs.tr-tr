---
title: Adlandırma Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afcaca34c937cc5a90c78a6f4de69ec395df4f42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649190"
---
# <a name="naming-warnings"></a>Adlandırma Uyarıları

Adlandırma uyarıları, .NET Tasarım Yönergelerinin adlandırma kurallarına uygunluğunu destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1700: Numaralandırma değerlerini 'Ayrılmış' olarak adlandırmayın](../code-quality/ca1700.md)|Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır.|
|[CA1713: Olaylarda önce veya sonra önek olmamalıdır](../code-quality/ca1713.md)|Olay adı "Önce" veya "Sonra" ile başlar. Belirli bir sırayla ilgili olayları adlandırmak için şimdiki veya geçmiş zamanı göreceli konumun sıralı eylemlerini belirtmek için kullanın.|
|[CA1714: Bayrak numaralandırmalarında çoğul adlar olmalıdır](../code-quality/ca1714.md)|Genel numaralandırmanın System. FlagsAttribute özniteliği ve adı "s" ile bitmiyor. FlagsAttribute ile işaretlenen türlerin, öznitelik birden fazla değerin belirtibileceğini gösterdiği için çoğul olan adlara sahip olması gerekir.|
|[CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)|Dışarıdan görünen bir tanımlayıcı ad Microsoft yazım denetimi kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.|
|[CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708.md)|Ortak dil çalışma zamanı hedef dilleri büyük/küçük harf duyarlı olması gerekmediğinden ad alanları, türler, üyeler ve parametreler için tanımlayıcılar yalnızca büyük/küçük harfe göre farklılık göstermeyebilir.|
|[CA1715: Tanımlayıcıların önekleri doğru olmalıdır](../code-quality/ca1715.md)|Dışarıdan görünen bir arabirimin adı, büyük bir "I" ile başlamıyor.  Dışarıdan görünen bir tür veya yöntemde genel tür parametresinin adı, büyük bir "T" ile başlamıyor.|
|[CA1720: Tanımlayıcılar tür adları içermemelidir](../code-quality/ca1720.md)|Parametre adı dışarıdan görünen üye, veri türü adını içerir ya da açıkça görünen üyenin adı dil özellikli veri türü adı içerir.|
|[CA1722: Tanımlayıcıların önekleri yanlış olmamalıdır](../code-quality/ca1722.md)|Kural gereği, programlama öğelerinin belirli bir önek ile başlayan adları vardır.|
|[CA1711: Tanımlayıcıların sonekleri yanlış olmamalıdır](../code-quality/ca1711.md)|Kural gereği, yalnızca, belirli temel türleri genişleten veya bazı arabirimleri ya da bu türlerinden türetilmiş türleri uygulayan tür adları belirli ayrılmış öneklerle bitmelidir. Diğer tür adları aşağıdaki ayrılmış sonekleri kullanmamalı.|
|[CA1717: Yalnızca FlagsAttribute numaralandırmalarında çoğul adlar olmalıdır](../code-quality/ca1717.md)|Adlandırma kuralları numaralandırma için adlandırma aynı anda birden fazla numaralandırma değeri olduğunu gösterir.|
|[CA1725: Parametre adları taban yöntem ile eşleşmelidir](../code-quality/ca1725.md)|Parametreyi geçersiz kılma hiyerarşisinde tutarlı adlandırma yöntemini geçersiz kılmaları kullanılabilirliği artırır. Temel bildirim alanındaki addan farklı türetilmiş yöntem parametre adı taban yöntemini geçersiz kılma veya yeni aşırı yöntemin yöntem olup olmadığı hakkında karışıklığa neden olabilir.|
|[CA1719: Parametre adları üye adlarıyla eşleşmemelidir](../code-quality/ca1719.md)|Bir parametre adı bir parametrenin anlamını iletmeli ve üye adı bir üyenin anlamını iletmelidir. Bunların aynı olduğu yerlerde nadir bir tasarım olur. Aynı üye adıyla parametreyi adlandırma sezgisel değildir ve kütüphane kullanımını zorlaştırır.|
|[CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701.md)|Kaynak dizesindeki her sözcük büyük küçük harfe dayalı belirteçlere bölünür. Her bir bitişik ikili-işaret kombinasyonu Microsoft yazım kitaplığı tarafından denetlenir. Tanınırsa, kelime kural ihlali üretir.|
|[CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703.md)|Kaynak dizesi, Microsoft Yazım kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.|
|[CA1724: Tür Adları Ad Alanlarıyla Eşleşmemelidir](../code-quality/ca1724.md)|Tür adları .NET ad alanlarının adlarıyla eşleşmemelidir. Bu kuralın ihlali, kitaplığın kullanılabilirliğini azaltabilir.|
|[CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707.md)|Kural gereği, tanımlayıcı adlar alt çizgi (_) karakterini içermez. Bu kural ad alanlarını, türleri, üyeleri ve parametreleri denetler.|
|[CA1721: Tür adları alma metotlarıyla eşleşmemelidir](../code-quality/ca1721.md)|Ortak veya korumalı bir üye adı "Get" ile başlar ve aksi durumda ortak veya korumalı özellik adıyla eşleşir. "Get" yöntemlerinin ve özelliklerinin açıkça işlevlerinden ayırt edilebilen adları olması gerekir.|
|[CA1716: Tanımlayıcılar anahtar sözcüklerle eşleşmemelidir](../code-quality/ca1716.md)|Ad alanı adı veya tür adı ayrılmış anahtar sözcük bir programlama dili ile eşleşir. Tanımlayıcı adı ve türleri için ortak dil çalışma zamanı, hedef diller tarafından tanımlanan anahtar sözcüklerle aynı değildir.|
|[CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md)|Dışarıdan görünen bir tanımlayıcının adı, tercih edilen terim varolduğunda alternatif olarak bir terim içerir. Alternatif olarak ad, "Bayrak" veya "Bayraklar" terimini içerir.|
|[CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709.md)|Kural gereği, parametre adları ortası büyük harfleri, ad alanı, tür ve üye adları, Pascal büyük harfleri kullanır.|
|[CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702.md)|Tanımlayıcının adı birden çok sözcük içerir ve bu sözcüklerden en az biri büyük harf kullanımı hatasına maruz kalmış birleşik kelime olarak görülür.|
|[CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712.md)|Tür bilgilerinin geliştirme araçları tarafından sağlanması beklendiğinden, numaralandırma üyelerinin adlarına tür adı ön eki uygulanmaz.|
|[CA1710: Tanımlayıcıların sonekleri doğru olmalıdır](../code-quality/ca1710.md)|Kural gereği, belirli temel türleri genişleten veya belirli arabirimleri ya da bu türlerden türetilmiş türleri uygulayan türlerin adları, temel tür veya arabirimle ilişkili bir soneke sahiptir.|
