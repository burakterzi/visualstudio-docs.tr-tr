---
title: Özet görünümü-Izleme verileri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2f52f80cad4ce7678a832a7b76a75d8f2fd4460e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778225"
---
# <a name="summary-view---instrumentation-data"></a>Özet görünümü-izleme verileri
Özet görünümü, bir profil oluşturma çalıştırmasında en fazla performans maliyeti olan işlevlerle ilgili bilgileri görüntüler. Bildirim bağlantılarının ve rapor listelerinin açıklaması dahil daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Zaman çizelgesi grafiği
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturma sırasında profili oluşturulan uygulamanın işlemci (CPU) kullanımını gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümlerini Özet zaman çizelgesinden filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Etkin yol
 **Etkin yol** , en çok kullanılan yürütme yolunu görüntüler. İşlevin Işlev ayrıntıları görünümünü görüntülemek için bir işleve tıklayabilirsiniz. İşlevin diğer görünümlerini görüntülemek için, işlevine sağ tıklayın ve sonra listeden bir görünüme tıklayın.

 **Etkin yol** her bir işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Geçen kapsamlı süre yüzdesi**|İşlevin işlev gövdesinde ve çağrılan işlevlerde kod çalıştırırken harcadığı, profil oluşturma verilerinde tüm zamanın yüzdesi.|
|**Geçen dışlamalı süre yüzdesi**|İşlevin işlev gövdesinde kod yürütmeyi harcadığı, profil oluşturma verilerinde tüm zamanın yüzdesi. İşlevin çağrıldığı işlevlerde harcanan süre dahil değildir.|

## <a name="functions-with-most-individual-work"></a>En bireysel Işleri olan işlevler
 Çağrılan işlevlerde değil, işlevin gövdesinde kod yürütürken en çok kullanılan işlevlerin listesi.

 **En bireysel işleri olan işlevler** her bir işlev için aşağıdaki verileri içerir:

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|İşlevin adı.|
|**Dışlamalı zaman yüzdesi**|İşlevin işlev gövdesinde kod yürütmeyi harcadığı, profil oluşturma verilerinde tüm zamanın yüzdesi. İşlevin çağrıldığı işlevlerde harcanan süre dahil değildir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünümü-örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünümü-.NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
