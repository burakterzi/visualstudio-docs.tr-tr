---
title: Yük Testi Sanal Kullanıcı etkinliğini çözümleme
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bba807eae2a7767b9b4271d0df48e962a2113285
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665365"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisinin Ayrıntılar görünümündeki Yük Testi Sanal Kullanıcı etkinliğini çözümleme

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Sanal Kullanıcı etkinliği grafiği**

![Sanal Kullanıcı etkinliği grafiği](../test/media/virtual_actchart.png)

**Ayrıntılar** görünümü, tek tek sanal kullanıcıların yük testi sırasında ne yaptığını görsel olarak analiz etmek Için kullanılan **Sanal Kullanıcı etkinliği grafiğini**görüntüler. **Sanal Kullanıcı etkinliği grafiği** , Kullanıcı etkinliği düzenlerini, yük düzenlerini görmenizi, başarısız veya yavaş testlerin bağıntılı olduğunu ve diğer Sanal Kullanıcı etkinliğiyle istekleri görmenizi sağlar. **Sanal Kullanıcı etkinliği grafiği** , CPU kullanımında ani artışları, saniye başına isteklerin düşünü ve artışlar ve bırakılanlar sırasında hangi testlerin veya sayfaların çalıştığını belirlemenize de yardımcı olabilir.

> [!NOTE]
> **Sanal Kullanıcı etkinliği ayrıntıları grafiğini**kullanmak istediğiniz yük testini çalıştırmadan önce, yük performansı Testi Düzenleyicisi 'ni kullanarak, **Zamanlama Ayrıntıları Depolama** özelliğinin **allindividualdetails** seçeneğine ayarlandığını doğrulamanız gerekir.

**Ayrıntılar gösterge bölmesi**

![Ayrıntılar gösterge bölmesi](../test/media/ltest_detailslegend.png)

Ayrıntılar gösterge paneli **Sanal Kullanıcı etkinliği grafiğinde**görünür. Ayrıntılar gösterge bölmesi, birkaç farklı ölçüte göre testleri, sayfaları ve işlemleri filtrelemenizi sağlar. Örneğin, belirli testleri görünümden kaldırabilir veya tüm başarılı testleri kaldırabilir veya bazı hatalarda başarısız olan testleri kaldırabilirsiniz. Ayrıca, günlüğü olmayan tüm testleri de kaldırabilirsiniz.

Başarısız olan testleri vurgulayabilirsiniz, bu, başarısız olan tüm testleri kırmızı renkte görüntüler. Ayrıca, test günlükleri olan testleri vurgulayabilirsiniz. Günlükleri olan testler yeşil renkte görünür.

**Filtre sonuçları paneli**

![Filtre sonuçları paneli](../test/media/ltest_filterresults.png)

Filtre sonuçları paneli **Sanal Kullanıcı etkinliği grafiği**'nde görünür. Filtre sonuçları paneli aşağıdakilere filtre uygulayabilir:

- **Yalnızca günlükleri olan sonuçları göster** Yalnızca bunlarla ilişkili test günlükleri olan test sonuçlarını görüntüler.

- **Başarılı sonuçları göster** Başarılı sonuçları görüntüler.

- **Hatalı sonuçları göster** Hata ayıklamada yardımcı olabilecek hatalar içeren sonuçları görüntüler.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testinizi çalıştırın:** Bir yük testi oluşturduktan ve Sanal Kullanıcı etkinliği verilerini toplamayı etkinleştirecek şekilde yapılandırdıktan sonra, **Sanal Kullanıcı etkinliği grafiğini**görüntülemek için testi tamamlanana kadar testi çalıştırmanız gerekir.||
|**Sanal Kullanıcı etkinliği verilerini içeren yük testi sonuçlarını görüntüleyin:** Yük testiniz oluşturulduktan, yapılandırıldıktan ve çalışmayı tamamladıktan sonra, Sanal Kullanıcı **etkinlik grafiğini**kullanarak sanal kullanıcı etkinliği verilerini görüntüleyebilirsiniz.|[Yük testi sonuçlarını analiz](../test/analyze-load-test-results-using-the-load-test-analyzer.md) -   <br />-    [How: Yük testi sırasında sanal kullanıcıların ne yaptığını çözümleyin ](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Yük testlerinde performans sorunlarını yalıtın:** Yük testinizde performans sorunlarını yalıtmaya yardımcı olması için **Sanal Kullanıcı etkinliği grafiğini** kullanabilirsiniz.|-    [Walkthrough: Sorunları yalıtmak için Sanal Kullanıcı etkinliği grafiğini kullanma ](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)