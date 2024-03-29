---
title: Etki Alanı Sınıflarının Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58b86452d9bfa00c9b107aa0b2748117c64a0384
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747478"
---
# <a name="properties-of-domain-classes"></a>Etki Alanı Sınıflarının Özellikleri
Etki alanı sınıfları aşağıdaki tabloda yer alan özelliklere sahiptir. Etki alanı sınıfları hakkında daha fazla bilgi için bkz. [modelleri, sınıfları ve Ilişkileri anlama](../modeling/understanding-models-classes-and-relationships.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim değiştiricisi|Etki alanı sınıfına erişim düzeyi (`public` veya `internal`).|`public`|
|Özel Öznitelikler|Bu etki alanı sınıfından oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none >|
|Double türevi üretir|@No__t_0, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Özel Oluşturucusu vardır|@No__t_0, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Devralma değiştiricisi|Etki alanı sınıfından oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|`none`|
|Temel sınıf|Bu alan sınıfı türetildiyse, taban sınıfın adı.|\<none >|
|Name|Bu alan sınıfının adı.|Geçerli ad|
|Ad Alanı|Bu alan sınıfının ad alanı.|Geçerli ad alanı|
|Notlar|Bu alan sınıfıyla ilişkili resmi olmayan notlar.|\<none >|
|Açıklama|Oluşturulan tasarımcının Kullanıcı arabirimini belgelemek için kullanılan açıklama.|\<none >|
|Görünen ad|Bu alan sınıfı için oluşturulan tasarımcıda görüntülenecek ad.|\<none >|
|Help anahtar sözcüğü|Bu etki alanı sınıfına yönelik F1 yardımını indekslemek için kullanılan isteğe bağlı anahtar sözcük.|\<none >|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)