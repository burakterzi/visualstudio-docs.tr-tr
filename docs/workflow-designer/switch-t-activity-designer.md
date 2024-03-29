---
title: İş Akışı Tasarımcısı-anahtar <T> etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1afda542dd3f45e5be723ce35b2546626f3679e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649893"
---
# <a name="switcht-activity-designer"></a>@No__t_0T > etkinlik tasarımcısına anahtar

@No__t_0 etkinliği belirtilen bir ifadeyi değerlendirir ve aktiviteyi, ilişkili anahtarı değerlendirmeden elde edilen değerle eşleşen bir etkinlik koleksiyonundan yürütür.

**< T \>** etkinlik tasarımcısı, iş akışı Tasarımcısı <xref:System.Activities.Statements.Switch%601> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-switchtactivity"></a>Anahtar \<T > etkinliği

Bir <xref:System.Activities.Statements.Switch%601> etkinlik <xref:System.Activities.Statements.Switch%601.Expression%2A> ve <xref:System.Activities.Statements.Switch%601.Cases%2A> sözlüğünü içerir. Sözlükteki her bir durum, bir *anahtar* ve karşılık gelen *değeri*olarak hizmet veren bir etkinlik içeren bir çiftin oluşur. @No__t_0 etkinliği <xref:System.Activities.Statements.Switch%601.Expression%2A> değerlendirir ve anahtarların her birine karşı karşılaştırır. Bir eşleşme bulunursa ilgili etkinlik yürütülür. Sözlük anahtarlarının, sözlüğün eşitlik karşılaştırıcısı tarafından tanımlanan eşitlik türüne göre benzersiz olması gerektiğinden yalnızca bir eşleşme mümkündür. Hiçbir eşleşme bulunmazsa <xref:System.Activities.Statements.Switch%601.Default%2A> etkinlik yürütülür.

## <a name="how-to-use-the-switcht-activity-designer"></a>Anahtar \<T > etkinlik tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisinde **anahtar \<T >** etkinlik tasarımcısına erişin. İş Akışı Tasarımcısı, kullanıcının <xref:System.Activities.Statements.Switch%601> etkinliğinde kullanılan genel tür *T* 'yi belirtmesini sağlamak Için **türleri Seç** iletişim kutusunu görüntüler. Varsayılan değer **Int32**'dir. Genel tür *t* seçildikten sonra, iş akışı tasarımcısına bir **anahtar < T \>** Tasarımcısı eklenir.

**Anahtar < T \>** Tasarımcısı 'nın özellikleri aşağıda verilmiştir. Bu özelliklerin tümü, özellik kılavuzunda düzenlenebilir. Bunlardan bazıları tasarımcı yüzeyi üzerinde de düzenlenebilir.

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.Switch%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer < Int32 \> anahtarıdır. Değer, **Özellikler** penceresinde veya doğrudan tasarımcı üstbilgisinde düzenlenebilir.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Doğru|Hangi durumun yürütüleceğini öğrenmek için servis talepleri koleksiyonundaki anahtarlarla karşılaştırmak için kullanılan ifadeyi belirtir.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Hiçbir eşleşme bulunmazsa yürütülen etkinliği belirtir. Etkinliğin bırakılbileceği **varsayılan** kutuyu açmak için tasarımcıda **etkinlik Ekle** düğmesine tıklayın.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Değerlendirilecek çalışmaları belirtir. Bir durum eklemek için, **anahtar \<T >** Tasarımcısı ' nın altındaki **yeni durum Ekle** düğmesine tıklayın. Düğme, anahtar ekleme sırasında seçilen genel tür bir metin kutusuna (\<T > dize veya Enum) olarak değişir. **Case değer** kutusuna bir anahtar eklendikten sonra, Case alanı genişler ve bir etkinlik, durum için yürütme mantığını tanımlamak üzere ipucu metninde "etkinliği buraya bırak" olarak da çalıştırılabilir.|

Büyük/küçük harf anahtarları yinelenmediğinden, birden çok durum eklenebilir. Aksi halde, belirtilen Case anahtarının zaten var olduğunu ve farklı bir anahtar seçmeniz gerektiğini bildiren bir hata iletişim kutusu görüntülenir. **Switch \<T >** tasarımcısında, tek seferde yalnızca bir Case alanı genişletilmiş görünümde olabilir. Bir Case alanı daraltılmış görünümdayken, büyük/küçük harfe tıklamak onu genişletir. Daraltılan bir durumda tasarımcı, etkinliğin görünen adını, varsa sağ taraftaki büyük küçük harf olarak gösterir. Aksi takdirde, bu durum, tıkladığınızda ve bir etkinlik eklemenize olanak varsa, bu durumu genişleten **bir etkinlik Ekle** düğmesi gösterir.

Mevcut durumda olan anahtara tıkladığınızda, bir etiketten anahtar TextBox olarak değişir. böylece, Case anahtarını düzenleyebilmenizi sağlayabilirsiniz.

Bir servis talebi silmenin 2 yolu vardır:

- Büyük/küçük harf ' i seçin ve silin.

- Büyük/küçük harf ' i seçin, sağ tıklayarak bağlam menüsünü görüntüleyin ve **Sil**' i seçin.

Silmek için büyük/küçük harf ' i seçmeniz gerektiğini unutmayın. Etkinlik yalnızca bir servis talebi içinde seçilip silindiğinde etkinlik yalnızca durum değil olarak silinir.

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)