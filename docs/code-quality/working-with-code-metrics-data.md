---
title: Kod ölçümleri penceresi
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0824fe608ad1bac86ef904702bd1be907bc9ce7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649004"
---
# <a name="use-the-code-metrics-results-window"></a>Kod ölçümleri sonuçları penceresini kullanın

**Kod ölçümleri sonuçları** penceresinde, kod ölçüm Analizi tarafından oluşturulan veriler görüntülenir. Kod ölçümleri veri değerleri hakkında daha fazla bilgi için bkz. [kod ölçüm değerleri](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Kod ölçümleri sonuçlarını görüntüle

Kod **ölçümleri sonuçları penceresi,** kod ölçümleri sonuçları oluştururken otomatik olarak görüntülenir. Ayrıca, pencereyi istediğiniz zaman da görüntüleyebilirsiniz.

Aşağıdaki menü dizilerinden birini kullanarak kod ölçümleri sonuçları penceresini görüntüleyebilirsiniz:

- **Çözümle** menüsünde **Windows** > **Kod ölçümleri sonuçları**' nı seçin.

- **Görünüm** menüsünde **diğer Windows** > **Kod ölçümleri sonuçları**' nı seçin.

**Kod ölçümleri sonuçları** penceresi, hiçbir sonuç içermediğinden bile açılır.

### <a name="to-view-code-metrics-details"></a>Kod ölçümleri ayrıntılarını görüntülemek için

Kod ölçümleri sonuçları oluşturulduysa, **hiyerarşi** sütunundaki ağacı genişletin.

## <a name="filter-code-metrics-results"></a>Kod ölçümleri sonuçlarını filtrele

Üstteki araç çubuğunu kullanarak, **Kod ölçümleri sonuçları** penceresinde görüntülenen sonuçlara filtre uygulayabilirsiniz. Örneğin, yalnızca 65 altındaki bakım dizinine sahip sonuçları görmek isteyebilirsiniz.

**Filtre** açılan kutusu, sonuçlar sütunlarının adlarını içerir. Bir filtre tanımlandığında, listenin sonuna girintileme ile birlikte eklenir. Listede, tanımlanan son 10 filtre bulunabilir.

### <a name="to-filter-the-code-metrics-results"></a>Kod ölçümleri sonuçlarını filtrelemek için

1. **Filtre** listesinden sütun adını seçin.

2. **En**az, görüntülenecek en düşük değeri yazın.

3. **En**fazla, görüntülenecek en büyük değeri yazın.

4. **Filtre Uygula** düğmesine tıklayın.

5. Sonuç ayrıntılarını görmek için hiyerarşi ağacını genişletin.

## <a name="add-remove-and-rearrange-data-columns"></a>Veri sütunları ekleme, kaldırma ve yeniden düzenleme

**Kod ölçümleri sonuçları** penceresinden sonuç sütunları ekleyebilir veya kaldırabilirsiniz. Ayrıca, sonuçlar sütunlarını istediğiniz sırada görünecek şekilde yeniden düzenleyebilirsiniz.

### <a name="add-or-remove-a-column"></a>Sütun ekleme veya kaldırma

1. Sütun **Ekle/Kaldır** düğmesine tıklayın veya herhangi bir sütun başlığına sağ tıklayıp **sütun Ekle/Kaldır**' a tıklayın.

1. **Sütun Ekle/Kaldır** iletişim kutusunda, eklemek veya kaldırmak istediğiniz sütunun onay kutusunu seçin veya temizleyin ve ardından **Tamam**' ı seçin.

### <a name="rearrange-columns"></a>Sütunları yeniden Düzenle

1. **Sütun Ekle/Kaldır** düğmesine tıklayın.

1. **Sütun Ekle/Kaldır** iletişim kutusunda, taşımak istediğiniz sütunu seçin ve ardından yukarı oku veya aşağı oku seçin.

1. Sütun istediğiniz yere konumlandırıldığında **Tamam**' ı seçin.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Verileri panoya veya Excel 'e kopyalama

Seçilen bir kod Ölçüm verisi satırını, her bir veri sütununun adı ve değeri için bir satır içeren bir metin dizesi olarak Pano 'ya seçip kopyalayabilirsiniz. Ayrıca, tüm kod ölçümleri sonuçlarının bir Excel elektronik tablosuna aktarılması için **Microsoft Excel 'de seçimi aç** ' a tıklayabilirsiniz.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Kod ölçümü sonuçlarına göre iş öğesi oluşturma

**Kod ölçümü sonuçları** penceresindeki sonuçlara dayalı bir [Azure boards](/azure/devops/boards/index?view=vsts) iş öğesi oluşturabilirsiniz. İş öğesi oluşturulduğunda, Visual Studio otomatik olarak **başlık** alanına bir başlık girer ve **geçmiş** sekmesinin altındaki kod ölçüm verilerini otomatik olarak girer.

Azure Boards iş öğeleri hakkında daha fazla bilgi için bkz. [iş öğeleri](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Bir sonuca göre iş öğesi oluşturmak için

1. Sonuca sağ tıklayın.

2. **Iş öğesi oluştur**' un üzerine gelin ve sonra oluşturmak istediğiniz iş öğesi türüne (**hata**, **görev**vb.) tıklayın.

3. Tüm gerekli alanları doldurarak iş öğesi formunu doldurun.

4. **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayarak iş öğesini kaydedin.

### <a name="to-create-a-bug-based-on-a-result"></a>Bir sonuca dayalı bir hata oluşturmak için

1. Seçmek için sonuca tıklayın.

2. **Iş öğesi oluştur** düğmesine tıklayın.

3. Tüm gerekli alanları doldurarak iş öğesi formunu doldurun.

4. **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayarak iş öğesini kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçüm değerleri](../code-quality/code-metrics-values.md)
- [Nasıl yapılır: kod ölçümleri verileri oluşturma](../code-quality/how-to-generate-code-metrics-data.md)
