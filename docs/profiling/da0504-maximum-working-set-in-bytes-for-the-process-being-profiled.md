---
title: 'DA0504: Işlem için bayt cinsinden en yüksek çalışma kümesi profili oluşturuldu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a181ecb66c3735eb34ab3c866c3c68b2397781f6
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779330"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: İşlem için izin verilen Bayt Cinsinden En Büyük Çalışma Kümesinin profili oluşturuluyor

|||
|-|-|
|Kural Kimliği|DA0504|
|Kategori|Kaynak yönetimi|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmıştı. Işlem çalışma kümesi sayacı, profil oluşturduğunuz işlem tarafından fiziksel bellek kullanımını ölçer. Bildirilen değer tüm ölçüm aralıklarında gözlemlenen en yüksek değerdir.|
|Kural türü|Bilgisi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemin Şu anda kullandığı maksimum fiziksel bellek miktarını bayt cinsinden bildirir. İşlem çalışma kümesi, şu anda fiziksel bellekte bulunan işlem adres alanından sayfaları temsil eder. Bu kural, profil oluşturma etkinken işlem çalışma kümesi için en büyük değeri raporlar.

 Raporlanan değer, paylaşılan bellek segmentlerinden işleme başvurduğu yerleşik sayfaları içerir. İşlemin başvurduğu paylaşılan DLL 'Ler, sayılan paylaşılan bellek kesimlerine dahil edilir. İşlem çalışma kümesinin değeri, paylaşılan bellek kesimleri nedeniyle işlemin ayırdığı sanal bellek miktarından daha yüksek olabilir.

 İşlem çalışma kümesinin boyutu, işlemin etkin bir şekilde ne kadar sanal bellek kullandığını yansıtır. Ayrıca, uygulamayı çalıştırmak için kullanılabilir fiziksel bellek miktarı (veya RAM) ve diğer çalışan işlemlerden bu fiziksel bellek için çekişmeden da etkilenir. İşlem çalışma kümeleri hakkında daha fazla bilgi için bkz. MSDN 'nin Windows bellek yönetimi belgelerindeki [çalışma kümesi](/windows/win32/memory/working-set) .

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Kural, Windows performans izleme tesisinden Bu ölçüm verilerini toplar ve yalnızca bilgi için raporlar. Programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı test senaryoları altında uygulamanın performansını anlamak için kullanın.

 Profil oluşturma verilerinin [Işaretler görünümüne](../profiling/marks-view.md) gitmek için hata Listesi penceresindeki iletiye çift tıklayın. **Process\çalışma kümesi** ve **bellek \ Sayfa/sn** sayaç sütunlarını bulun. Ardından, **Process\working kümesinin** en büyük değerini bulun ve **bellek \ Sayfa/sn** değeriyle karşılaştırın. Genellikle, çalışma kümesi en yüksek değeri, özellikle makine bellekle sınırlı olduğunda, disk belleği GÇ etkinliğinin düşürüldüğü bir aralıkla ilişkilendirilir.
